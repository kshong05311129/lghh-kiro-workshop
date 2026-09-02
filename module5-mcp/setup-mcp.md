# MCP 설정하기

> 🎯 서로 다른 성격의 MCP 2개를 연결해봅시다! (5분)

> ⚠️ MCP 서버를 실행하려면 `uvx`가 필요한데, **환경 설정(Step 3)에서 이미 설치**했습니다. 터미널에서 `uvx --version`을 입력해 잘 설치되어 있는지만 확인하세요. 버전이 안 나오면 [환경 설정 Step 3](../introduction/getting-started.md)의 uv 설치를 다시 따라 하거나 강사에게 요청하세요.

## Step 1: 제품 DB 만들기

`product-db` MCP가 조회할 데이터베이스가 아직 없으니, [환경 설정 Step 6](../introduction/getting-started.md)에서 받아둔 `data/lghh_products_2026.csv`를 SQLite DB로 변환해달라고 Kiro에게 요청합니다. 채팅창에 아래를 입력하세요:

```
data/lghh_products_2026.csv 파일을 읽어서 data/lghh_products.db라는 이름의 SQLite 데이터베이스로 변환해줘.
테이블 이름은 products로 하고, CSV의 컬럼(brand, product_name, category, key_ingredients, price, launch_month, target, tier)을 그대로 사용해줘.
Python 표준 라이브러리(csv, sqlite3)만 사용해서 변환하고, CSV는 UTF-8 인코딩으로 읽어줘. 별도 패키지 설치는 하지 마.
```

> 💡 Kiro가 Python 스크립트를 작성해서 실행하는 과정을 보여줄 것입니다(추가 설치 없이 Step 3에서 설치한 Python으로 바로 됩니다). `data/lghh_products.db` 파일이 생겼다면 성공!

## Step 2: MCP 설정 파일 생성

> ⚠️ **MCP 설정 파일은 Kiro에게 "만들어줘"라고 시키면 안 됩니다.** `.kiro/settings/` 폴더는 보안상 AI가 절대 쓰기/수정할 수 없도록 막혀 있는 영역이라, 채팅으로 요청하면 항상 실패합니다. 아래처럼 **직접** 만들어주세요.

1. `Cmd+Shift+P`(Mac) 또는 `Ctrl+Shift+P`(Windows)로 명령 팔레트를 열고 **"Kiro: Open workspace MCP config (JSON)"** 를 입력해 선택합니다.
2. `.kiro/settings/mcp.json` 파일이 자동으로 생성되며 에디터에 열립니다.
3. 아래 내용을 **직접 붙여넣고**, 파일을 저장합니다 (`Cmd+S` / `Ctrl+S`):

```json
{
  "mcpServers": {
    "aws-docs": {
      "command": "uvx",
      "args": ["awslabs.aws-documentation-mcp-server@latest"],
      "timeout": 60000
    },
    "product-db": {
      "command": "uvx",
      "args": ["mcp-server-sqlite", "--db-path", "data/lghh_products.db"],
      "timeout": 60000
    }
  }
}
```

> 💡 `aws-docs`는 AWS 공식 문서를 검색·조회하는 MCP, `product-db`는 Step 1에서 만든 사내 제품 DB(`data/lghh_products.db`)를 조회하는 MCP입니다. `timeout`은 서버가 처음 뜨는 데 걸리는 시간(밀리초)을 기다려주는 값이라, 60000(60초)은 되어야 `uvx`가 패키지를 내려받아 첫 실행할 시간을 벌 수 있습니다.

## Step 3: MCP 서버 활성화

1. 파일 저장 후, Kiro를 **재시작** (File → Reload Window 또는 `Ctrl+Shift+P` → "Reload")
2. 왼쪽 하단 또는 설정에서 **MCP 서버 상태** 확인
3. `aws-docs`, `product-db` 둘 다 **Connected** ✅ 상태면 성공!

> 📸 _스크린샷 삽입: MCP 서버 Connected 상태 화면_

## Step 4: 동작 확인

채팅에 입력:

```
우리 제품 DB에서 브랜드별 제품 수와 평균 가격을 조회해줘
```

> 💡 AI가 DB에 쿼리를 실행해서 **실제 숫자로 된 결과**를 보여주면 `product-db` MCP가 정상 작동하는 것입니다!

## 🔧 트러블슈팅

### "Tool call denied by user's permissions"라는 에러가 떠요

* **정상입니다.** Kiro는 보안상 `.kiro/settings/` 폴더를 AI가 못 건드리게 막아놨습니다. AI에게 mcp.json을 만들어달라고 시켜서 나는 에러이니, Step 2 안내대로 명령 팔레트로 파일을 열어 **직접** 수정하세요.

### "MCP 서버가 연결 안 돼요"

* `uvx` 설치 여부 확인: 터미널에서 `uvx --version`
* Kiro 재시작
* `.kiro/settings/mcp.json` 경로와 JSON 문법(쉼표, 중괄호) 확인
* `timeout` 값이 `60000`(밀리초) 이상인지 확인 — 값이 너무 작으면 서버가 뜨기도 전에 타임아웃 납니다

### "product-db 연결이 안 돼요"

* `data/lghh_products.db` 파일이 프로젝트 폴더에 있는지 확인 (없다면 "data 폴더 안에 lghh_products.db 파일이 있는지 확인해줘"라고 Kiro에 요청)
* Kiro를 프로젝트 루트 폴더(Step 5에서 만든 `kiro-beauty-workshop`)에서 열었는지 확인 — 경로가 어긋나면 DB를 못 찾습니다
* (진행자 참고) `mcp-server-sqlite`는 2025년 5월 이후 유지보수가 중단(archived)된 패키지입니다. 지금도 설치·실행은 되지만, 당일 갑자기 설치가 안 되면 패키지 자체 이슈일 수 있으니 참가자에게 "원래 그런 것"이라 안내하고 넘어가세요.

### (Windows) "제품 DB 변환 중 한글이 깨지거나 에러가 나요"

* Windows 기본 인코딩(cp949) 때문에 발생할 수 있습니다. Step 1 프롬프트에 있는 "UTF-8 인코딩으로 읽어줘" 문구를 빼지 말고 그대로 입력했는지 확인하세요.
* 그래도 안 되면 "data/lghh_products.db를 지우고, CSV를 UTF-8로 명시해서 다시 변환해줘"라고 Kiro에 다시 요청하세요.

### "조회/검색이 안 돼요"

* 인터넷 연결 확인 (aws-docs는 인터넷 필요)
* MCP 서버 상태가 "Connected"인지 확인
* 30초 정도 기다려보세요 (최초 연결 시 시간 소요)

***

> ✅ MCP 연결 완료! 이제 실습으로 넘어갑시다.

👉 다음: [MCP 활용 실습](mcp-practice.md)
