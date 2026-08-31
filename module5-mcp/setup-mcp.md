# MCP 설정하기

> 🎯 웹 검색 MCP를 연결해봅시다! (5분)

> ⚠️ MCP 서버를 실행하려면 `uvx`가 필요한데, **환경 설정(Step 3)에서 이미 설치**했습니다. 터미널에서 `uvx --version`을 입력해 잘 설치되어 있는지만 확인하세요. 버전이 안 나오면 [환경 설정 Step 3](../introduction/getting-started.md)의 uv 설치를 다시 따라 하거나 강사에게 요청하세요.

## Step 1: MCP 설정 파일 생성

Kiro 채팅창에 아래를 입력하세요:

```
.kiro/mcp.json 파일을 만들어줘. 내용은 아래와 같아:

{
  "mcpServers": {
    "web-search": {
      "command": "uvx",
      "args": ["duckduckgo-mcp-server"],
      "timeout": 30
    }
  }
}
```

## Step 2: MCP 서버 활성화

1. 파일 저장 후, Kiro를 **재시작** (File → Reload Window 또는 `Ctrl+Shift+P` → "Reload")
2. 왼쪽 하단 또는 설정에서 **MCP 서버 상태** 확인
3. `web-search`가 **Connected** ✅ 상태면 성공!

> 📸 _스크린샷 삽입: MCP 서버 Connected 상태 화면_

## Step 3: 동작 확인

채팅에 입력:

```
설화수 자음생 에센스 최신 리뷰를 웹에서 검색해서 정리해줘
```

> 💡 AI가 **"웹을 검색 중..."** 이라는 메시지를 보여주면 MCP가 정상 작동하는 것입니다!

## 🔧 트러블슈팅

### "MCP 서버가 연결 안 돼요"

* `uvx` 설치 여부 확인: 터미널에서 `uvx --version`
* Kiro 재시작
* `.kiro/mcp.json` 경로 확인

### "검색이 안 돼요"

* 인터넷 연결 확인
* MCP 서버 상태가 "Connected"인지 확인
* 30초 정도 기다려보세요 (최초 연결 시 시간 소요)

***

> ✅ MCP 연결 완료! 이제 실습으로 넘어갑시다.

👉 다음: [MCP 활용 실습](mcp-practice.md)
