# MCP 설정하기

> 🎯 서로 다른 성격의 MCP 2개를 연결해봅시다! (5분)

> ⚠️ MCP 서버를 실행하려면 `uvx`가 필요한데, **환경 설정(Step 3)에서 이미 설치**했습니다. 터미널에서 `uvx --version`을 입력해 잘 설치되어 있는지만 확인하세요. 버전이 안 나오면 [환경 설정 Step 3](../introduction/getting-started.md)의 uv 설치를 다시 따라 하거나 강사에게 요청하세요.

## Step 1: 제품 DB 만들기

`product-db` MCP가 조회할 데이터베이스가 아직 없으니, [환경 설정 Step 6](../introduction/getting-started.md)에서 받아둔 `data/lghh_products_2026.csv`를 SQLite DB로 변환해달라고 Kiro에게 요청합니다. 채팅창에 아래를 입력하세요:

```
data/lghh_products_2026.csv 파일을 읽어서 data/lghh_products.db라는 이름의 SQLite 데이터베이스로 변환해줘.
테이블 이름은 products로 하고, CSV의 컬럼(brand, product_name, category, key_ingredients, price, launch_month, target, tier)을 그대로 사용해줘.
```

> 💡 Kiro가 Python 스크립트를 작성해서 실행하는 과정을 보여줄 것입니다. `data/lghh_products.db` 파일이 생겼다면 성공!

## Step 2: MCP 설정 파일 생성

Kiro 채팅창에 아래를 입력하세요:

```
.kiro/mcp.json 파일을 만들어줘. 내용은 아래와 같아:

{
  "mcpServers": {
    "aws-docs": {
      "command": "uvx",
      "args": ["awslabs.aws-documentation-mcp-server@latest"],
      "timeout": 30
    },
    "product-db": {
      "command": "uvx",
      "args": ["mcp-server-sqlite", "--db-path", "data/lghh_products.db"],
      "timeout": 30
    }
  }
}
```

> 💡 `aws-docs`는 AWS 공식 문서를 검색·조회하는 MCP, `product-db`는 우리가 Step 6에서 받아둔 `lghh_products_2026.csv`를 미리 변환해둔 사내 제품 DB(`data/lghh_products.db`)를 조회하는 MCP입니다.

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

### "MCP 서버가 연결 안 돼요"

* `uvx` 설치 여부 확인: 터미널에서 `uvx --version`
* Kiro 재시작
* `.kiro/mcp.json` 경로 확인

### "product-db 연결이 안 돼요"

* `data/lghh_products.db` 파일이 프로젝트 폴더에 있는지 확인 (없다면 "data 폴더 안에 lghh_products.db 파일이 있는지 확인해줘"라고 Kiro에 요청)
* Kiro를 프로젝트 루트 폴더(Step 5에서 만든 `kiro-beauty-workshop`)에서 열었는지 확인 — 경로가 어긋나면 DB를 못 찾습니다

### "조회/검색이 안 돼요"

* 인터넷 연결 확인 (aws-docs는 인터넷 필요)
* MCP 서버 상태가 "Connected"인지 확인
* 30초 정도 기다려보세요 (최초 연결 시 시간 소요)

***

> ✅ MCP 연결 완료! 이제 실습으로 넘어갑시다.

👉 다음: [MCP 활용 실습](mcp-practice.md)
