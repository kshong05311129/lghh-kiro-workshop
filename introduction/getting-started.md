# 환경 설정

> ⏱️ 소요시간: 약 15분

## 📋 체크리스트

시작하기 전에 아래 항목을 확인하세요:

* [ ] 노트북 준비 (Windows 또는 Mac)
* [ ] 인터넷 연결 확인
* [ ] Kiro IDE 설치 완료
* [ ] Python / Node.js / uv 설치 완료
* [ ] 로그인 완료
* [ ] 실습 데이터 다운로드 완료

## Step 1: Kiro IDE 다운로드 🔧

### 다운로드 링크

👉 [https://kiro.dev/downloads](https://kiro.dev/downloads)

운영체제에 맞는 버전을 다운로드합니다:

* **Windows**: `.exe` 파일
* **Mac (Intel)**: `.dmg` 파일 (Intel)
* **Mac (Apple Silicon)**: `.dmg` 파일 (Apple Silicon)

> 💡 Mac 칩 확인법: 좌상단 🍎 → "이 Mac에 관하여" → 칩 확인

<figure><img src="../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

## Step 2: 설치하기

### Windows

1. 다운로드한 `.exe` 파일 더블클릭
2. "다음" 계속 클릭
3. 설치 완료!

### Mac

1. 다운로드한 `.dmg` 파일 더블클릭
2. Kiro 아이콘을 Applications 폴더로 드래그
3. Applications에서 Kiro 실행

> 💡 설치가 안 되면 손 들어주세요! 진행자가 도와드립니다. 🙋

## Step 3: 필수 프로그램 설치 (Python / Node.js / uv) [🐍](https://claude.ai/code/artifact/887e8b28-d148-47af-9d8f-cfa2cf8e77c2)

> 💡 Kiro가 코드를 만든 뒤 문법 오류가 없는지 스스로 확인하면서, 가끔 Python이나 Node.js를 자동으로 실행합니다. 미리 설치해두면 이 과정이 매끄럽게 진행됩니다.

### 💬 이게 다 뭔가요? (프로그래밍 몰라도 OK)

* **Python / Node.js**: Kiro가 만든 코드를 컴퓨터에서 직접 실행시켜주는 프로그램입니다. Python은 파이썬 언어로 쓰인 코드를, Node.js는 자바스크립트(JavaScript)라는 언어로 쓰인 코드를 실행합니다. Kiro가 코드를 만든 뒤 실제로 잘 작동하는지 돌려보며 확인할 때 이 둘 중 하나가 필요합니다.
* **uv**: Python으로 만들어진 작은 프로그램들을 빠르게 설치하고 실행해주는 보조 도구입니다. 오늘 워크샵 뒷부분(Module 5: MCP 연동)에서 AI에게 사내 제품 DB 조회, AWS 공식 문서 검색 같은 외부 기능을 연결할 때 사용합니다.

지금은 "설치만" 해두고, 실제로 어떻게 쓰이는지는 각 모듈에서 자연스럽게 보게 됩니다.

### Windows

> 💡 아래 3개는 \*\*명령 프롬프트(cmd)\*\*에서 winget 명령 하나씩으로 설치합니다. 명령 프롬프트를 처음 열어보신다면 아래 순서를 따라 하세요.
>
> 1. 키보드에서 **윈도우 키**를 누릅니다 (시작 메뉴가 열립니다)
> 2. `cmd`라고 입력합니다 ("명령 프롬프트" 앱이 검색 결과에 나타납니다)
> 3. \*\*"명령 프롬프트"\*\*를 클릭(또는 Enter)해서 실행합니다
> 4. 검은 화면의 창이 열리면 준비 완료입니다 — 아래 명령들을 여기에 입력하세요
>
> 설치 도중 "이 앱이 디바이스를 변경할 수 있도록 허용하시겠습니까?" 같은 창이 뜨면(특히 Node.js 설치 시) \*\*"예"\*\*를 클릭하면 됩니다 — 필요할 때만 winget이 알아서 권한을 요청하는 것이니 당황하지 마세요.
>
> <img src="../.gitbook/assets/image (25).png" alt="" data-size="original">

1.  **Python**: 먼저 이미 설치되어 있는지 확인합니다 (Windows는 `python3`가 아니라 `python`입니다).

    ```bash
    python --version
    ```

    버전이 나오면 이미 설치된 것이니 아래 설치는 건너뛰세요. **버전이 안 나올 때만** 설치합니다:

    ```bash
    winget install Python.Python.3.13
    ```

    > <img src="../.gitbook/assets/image (21).png" alt="" data-size="original">

    <div data-gb-custom-block data-tag="hint" data-style="danger" class="hint hint-danger"><p>설치 후 <strong>반드시 새 터미널 창을 열어서</strong> 다시 확인하세요. 설치 전에 이미 열려있던 터미널은 PATH가 갱신되지 않아서 "안 된다"고 착각하기 쉽습니다.</p></div>

    ```bash
    python --version
    ```

    > <img src="../.gitbook/assets/image (24).png" alt="" data-size="original">

    * 그래도 `python`이 안 먹히면? → 이 페이지 맨 아래 **🔧 트러블슈팅 → "python / node / uv 명령이 안 먹혀요"** 참고 (PATH 직접 등록하는 안전한 방법 있음)

    > 💡 **대안: 브라우저에서 설치하기** — [python.org/downloads/windows](https://www.python.org/downloads/windows/) 접속 → 맨 위 **"Download Python install manager"** 버튼은 누르지 말고(별도 관리 도구를 또 설치해야 하는 복잡한 방식), 아래로 스크롤해서 최신 버전 아래 **"Windows installer (64-bit)"** 클릭 → 설치 화면 하단 **"Add python.exe to PATH"** 체크박스 꼭 체크.
2.  [**Node.js**](https://claude.ai/code/artifact/93048e6a-72db-4fbe-adcf-20847edef5aa): 먼저 이미 설치되어 있는지 확인합니다.

    ```bash
    node --version
    ```

    버전이 나오면 건너뛰세요. **버전이 안 나올 때만** 설치합니다:

    ```bash
    winget install OpenJS.NodeJS.LTS
    ```

    설치 완료 후 새 터미널 창을 열어서 다시 확인하세요:

    ```bash
    node --version
    ```

    > <img src="../.gitbook/assets/image (22).png" alt="" data-size="original">

    > 💡 **대안: 브라우저에서 설치하기** — [nodejs.org](https://nodejs.org)에서 **LTS** 버전 다운로드 후, 기본 옵션 그대로 설치.
3.  **uv**: 먼저 이미 설치되어 있는지 확인합니다.

    ```bash
    uv --version
    ```

    버전이 나오면 건너뛰세요. **버전이 안 나올 때만**, Python 설치가 끝난 뒤 설치합니다:

    ```bash
    winget install astral-sh.uv
    ```

    설치 후 "Path environment variable modified; restart your shell" 메시지가 뜨면, 새 터미널 창을 열어서 다시 확인하세요:

    ```bash
    uv --version
    ```

    > <img src="../.gitbook/assets/image (23).png" alt="" data-size="original">

    > 💡 **대안**: `pip install uv`

> ⚠️ **`python`을 입력했는데 갑자기 Microsoft Store가 열려요?** Windows에만 있는 증상입니다. 설정 → 앱 → 고급 앱 설정 → **앱 실행 별칭**에서 `python.exe`, `python3.exe` 항목을 모두 꺼주세요. 그런 다음 터미널을 새로 열어 다시 시도하세요.

### Mac

1. **Python**: 대부분 기본 내장되어 있습니다. 터미널을 열어 `python3 --version`을 입력했을 때 버전이 나오면 OK. 처음 실행 시 "Install Command Line Developer Tools" 팝업이 뜨면 설치를 눌러주세요 (몇 분 소요될 수 있습니다).
2. **Node.js**: 터미널에서 `brew install node` (Homebrew가 없다면 [brew.sh](https://brew.sh) 참고)
3.  **uv**: 터미널에서 아래 명령을 입력합니다.

    ```bash
    brew install uv
    ```

> 💡 설치가 번거로우면 진행자에게 요청하세요! 워크샵 시작 전 미리 도와드릴 수 있습니다.

## Step 4: 로그인 🔑

> ⚠️ **중요**: 오늘 워크샵은 **AWS IAM Identity Center** 방식(회사 SSO 계정)으로 로그인합니다. 개인 계정이 아닌, **워크샵 진행자가 안내하는 Start URL과 계정 정보**를 사용하세요.

1. Kiro를 실행합니다
2. **"Sign in"** 버튼 클릭
3. **"Use IAM Identity Center"** 선택
4. 진행자가 안내한 **Start URL**을 입력
5. 브라우저가 열리면 제공된 계정으로 로그인
6. \*\*"Allow"\*\*를 클릭하여 Kiro 접근을 허용

```mermaid
graph TD
    A[Kiro 실행] --> B[Sign in 클릭]
    B --> C[Use IAM Identity Center 선택]
    C --> D[Start URL 입력]
    D --> E[브라우저에서 로그인]
    E --> F[Allow 클릭]
    F --> G[✅ 로그인 완료!]
```

> ⚠️ **Start URL이나 계정 정보를 모르겠다면?** 진행자에게 바로 문의하세요. 워크샵 시작 전 미리 배포된 안내문을 확인해보세요.

## Step 5: 프로젝트 폴더 만들기 📁

1. 바탕화면에 `kiro-beauty-workshop` 폴더를 만듭니다
2. Kiro에서 **File → Open Folder** 클릭
3. 방금 만든 `kiro-beauty-workshop` 폴더 선택

## Step 6: 실습 데이터 준비 📄

오늘 워크샵에서 계속 사용할 데이터 2개를 미리 받아둡니다. Kiro AI 채팅창에 아래를 각각 입력하세요:

```
아래 URL의 내용을 다운로드해서 data/lghh_products_2026.csv 파일로 저장해줘
https://raw.githubusercontent.com/kshong05311129/lghh-kiro-workshop/main/data/lghh_products_2026.csv
```

<figure><img src="../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>

```
아래 URL의 내용을 다운로드해서 data/beauty-brand-guide.md 파일로 저장해줘
https://raw.githubusercontent.com/kshong05311129/lghh-kiro-workshop/main/data/beauty-brand-guide.md
```

<figure><img src="../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

> 💡 CSV는 2026년 상반기 LG생활건강 가상 제품 데이터, 브랜드 가이드는 브랜드별 포지셔닝/톤앤매너 샘플 문서입니다. 이후 여러 모듈에서 반복해서 사용합니다.

## Step 7: 잘 되는지 확인하기 ✅

Kiro 화면에서 아래를 확인하세요:

* [ ] 왼쪽에 파일 탐색기가 보인다
* [ ] `data/` 폴더에 `lghh_products_2026.csv`, `beauty-brand-guide.md`가 보인다
* [ ] 오른쪽(또는 하단)에 AI 채팅창이 보인다

채팅창에 아래를 입력해보세요:

```
안녕하세요! 잘 작동하나요?
```

AI가 답변하면 성공입니다! 🎉

## 🔧 트러블슈팅

### "로그인이 안 돼요"

* Start URL을 정확히 입력했는지 확인
* 브라우저 팝업 차단이 되어있지 않은지 확인
* 진행자에게 계정 정보 재확인

### "Sign in 버튼이 안 보여요"

* Kiro를 완전히 종료 후 재실행해보세요

### "AI가 답변을 안 해요"

* 인터넷 연결 확인
* 로그인 상태 확인 (좌하단 계정 아이콘)

### "데이터 파일이 안 받아져요"

* 인터넷 연결 확인 후 다시 요청
* `data` 폴더가 없다면 "data 폴더 만들어줘"라고 먼저 요청

### "python / node / uv 명령이 안 먹혀요"

* Windows: `python --version`(⚠️ `python3`이 아닙니다), `node --version`, `uv --version`으로 확인. 안 나오면 아래 순서대로 시도하세요:
  1. **새 터미널 창을 열어서 다시 확인** (설치 전에 열어둔 터미널은 PATH가 갱신되지 않습니다 — 대부분 이걸로 해결됩니다)
  2. 그래도 안 되면 컴퓨터 재시작 후 다시 확인
  3. 그래도 안 되면 위 "Microsoft Store가 열려요" 항목(앱 실행 별칭) 확인
  4.  그래도 안 되면 PATH를 직접 등록합니다.

      <div data-gb-custom-block data-tag="hint" data-style="danger" class="hint hint-danger"><p><strong>반드시 <code>where python</code>으로 내 컴퓨터의 실제 경로를 먼저 확인하세요.</strong> 아래 명령의 경로(<code>Python313</code> 등)는 어디까지나 <strong>예시</strong>입니다. 확인 없이 예시 경로를 그대로 복사해서 실행하면, 실제로는 존재하지 않는 경로가 등록되어 오히려 안 될 수 있습니다.</p></div>

      ```cmd
      where python
      ```

      위 명령으로 나온 경로를 아래 `C:\Users\%USERNAME%\AppData\Local\Programs\Python\Python313` 자리에 **그대로 바꿔 넣어서** 실행합니다:

      ```cmd
      setx PATH "C:\Users\%USERNAME%\AppData\Local\Programs\Python\Python313;%PATH%"
      ```

      (버전이 다르면 `Python313` 부분만 `where python` 결과에 맞게 바꿔주세요. 적용 후 새 터미널 필요.)

      *   ⚠️ **그런데도 계속 안 되거나, 다른 프로그램(git 등) 명령어가 갑자기 같이 안 먹히면**: PATH가 1024자 넘어서 `setx`가 잘랐을 가능성이 있습니다. 이 경우 아래로 다시 등록하세요.

          ```cmd
          reg add "HKCU\Environment" /v Path /t REG_EXPAND_SZ /d "%PATH%;C:\Users\%USERNAME%\AppData\Local\Programs\Python\Python313" /f
          ```
      * 또는 (클릭으로 안전하게) **설정 → 시스템 정보 → 고급 시스템 설정 → 환경 변수 → 사용자 변수의 `Path` → 편집 → 새로 만들기**에서 같은 경로를 추가해도 됩니다.
* Windows에서 `python` 입력 시 Microsoft Store가 열리는 경우: 위 Step 3의 "앱 실행 별칭" 안내를 확인하세요.
* Mac: 터미널에서 `python3 --version`, `node --version`, `uv --version`으로 설치 여부 확인
* `uv` 설치가 안 되면 Python이 먼저 정상 설치되어 있는지 확인 후 `pip install uv`(Windows) / `brew install uv`(Mac)를 다시 시도하세요.
* 그래도 안 되면 진행자에게 요청하세요 — 이 부분이 없어도 워크샵 진행 자체는 가능합니다.

***

> 🎉 **준비 완료!** 이제 본격적으로 시작합시다!

👉 다음: [Module 1: Steering](../module1-steering/)
