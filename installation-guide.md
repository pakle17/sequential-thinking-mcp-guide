# Sequential Thinking MCP 설치 단계별 가이드

이 가이드는 Cursor에서 Sequential Thinking MCP를 단계별로 설치하는 방법을 자세히 설명합니다.

## 1단계: 필수 요구 사항 확인

### Node.js 및 npm 설치 확인

```bash
# 버전 확인
node -v
npm -v
```

Node.js와 npm이 설치되어 있지 않은 경우:

#### Windows에서 설치
1. [Node.js 공식 웹사이트](https://nodejs.org/)에서 LTS 버전 다운로드
2. 다운로드한 설치 파일 실행 및 설치 과정 진행
3. 명령 프롬프트를 열고 설치 확인:
   ```bash
   node -v
   npm -v
   ```

#### macOS에서 설치 (Homebrew 사용)
```bash
# Node.js와 npm 설치
brew install node

# 설치 확인
node -v
npm -v
```

## 2단계: OpenRouter API 키 획득

1. [OpenRouter 웹사이트](https://openrouter.ai/)에 가입/로그인
2. 대시보드에서 "API Keys" 섹션으로 이동
3. "Create API Key" 버튼 클릭하여 새 API 키 생성
4. 생성된 API 키를 안전한 곳에 복사해두기

## 3단계: OpenRouter MCP 서버 설치

Windows PowerShell 또는 macOS Terminal에서 다음 명령어 실행:

```bash
npx -y @smithery/cli@latest install @mcpserver/openrouterai --client cursor --config "{\"openrouterApiKey\":\"YOUR_API_KEY\",\"openrouterDefaultModel\":\"deepseek/deepseek-chat-v3-0324:free\"}"
```

위 명령어에서 `YOUR_API_KEY` 부분을 OpenRouter에서 발급받은 실제 API 키로 대체하세요.

만약 "client closed" 오류가 발생하면 타임아웃 값을 추가하여 다시 시도:

```bash
npx -y @smithery/cli@latest install @mcpserver/openrouterai --client cursor --config "{\"openrouterApiKey\":\"YOUR_API_KEY\",\"openrouterDefaultModel\":\"deepseek/deepseek-chat-v3-0324:free\"}" --timeout 60000
```

## 4단계: Sequential Thinking MCP 서버 설치

```bash
npx -y @smithery/cli@latest install @smithery-ai/server-sequential-thinking --client cursor --key YOUR_API_KEY
```

마찬가지로 `YOUR_API_KEY` 부분을 OpenRouter API 키로 대체하세요.

"client closed" 오류 발생 시:

```bash
npx -y @smithery/cli@latest install @smithery-ai/server-sequential-thinking --client cursor --key YOUR_API_KEY --timeout 60000
```

## 5단계: 설치 확인 및 활성화

1. Cursor 열기
2. 설정 메뉴 열기 (단축키: Ctrl + , 또는 Cmd + , on Mac)
3. MCP 섹션으로 이동
4. 서버 목록에서 다음 항목 확인:
   - "openrouterai"
   - "server-sequential-thinking"
5. **중요**: 각 서버의 상태가 "Disabled"로 표시된 경우, 클릭하여 "Enabled"로 변경해야 합니다.
6. 녹색 점이 나타나면 서버가 성공적으로 활성화된 것입니다.

## 설치 과정에서 자주 발생하는 문제

### 1. "client closed" 오류
- [troubleshooting.md](./troubleshooting.md)의 상세 해결 가이드를 참조하세요.

### 2. API 키 오류
- API 키가 올바르게 입력되었는지 확인
- OpenRouter 대시보드에서 API 키 유효성 확인
- API 키가 활성화되어 있는지 확인

### 3. 설치는 성공했지만 서버가 활성화되지 않는 경우
- Cursor 설정에서 서버가 "Disabled" 상태인지 확인하고, 클릭하여 "Enabled"로 변경
- Cursor 재시작 후 다시 시도
- MCP 서버 캐시 폴더 확인:
  - Windows: `%APPDATA%\Cursor\mcp\cache`
  - macOS: `~/Library/Application Support/Cursor/mcp/cache`

## 다음 단계: Sequential Thinking 사용하기

Sequential Thinking이 올바르게 설치되면:

1. Cursor에서 새 프로젝트나 파일 열기
2. 커맨드 팔레트 열기 (Ctrl+Shift+P 또는 Cmd+Shift+P)
3. "AI Chat" 명령 실행
4. 채팅 창에서 복잡한 문제나 단계별 해결이 필요한 질문 입력
5. Sequential Thinking이 활성화되어 있으면, 더 구조화된 단계별 사고 과정을 통해 답변을 제공합니다.

## 참고 자료

- [Cursor 공식 문서](https://cursor.sh/docs)
- [OpenRouter 문서](https://openrouter.ai/docs)
- [Smithery AI 문서](https://smithery.ai)
- [Sequential Thinking GitHub](https://github.com/smithery-ai/server-sequential-thinking)