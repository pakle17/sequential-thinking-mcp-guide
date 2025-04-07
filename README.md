# Cursor에서 Sequential Thinking MCP 설치 가이드

이 저장소는 Cursor에서 OpenRouter MCP 서버와 Sequential Thinking MCP 서버를 설치하는 방법과 발생할 수 있는 "client closed" 오류 해결 방법을 안내합니다.

## 필요 조건

1. Node.js 및 npm 설치
2. OpenRouter 계정 및 API 키 (https://openrouter.ai)

## 설치 방법

### 1. OpenRouter MCP 서버 설치

```bash
npx -y @smithery/cli@latest install @mcpserver/openrouterai --client cursor --config "{\"openrouterApiKey\":\"YOUR_API_KEY\",\"openrouterDefaultModel\":\"deepseek/deepseek-chat-v3-0324:free\"}"
```

위 명령어에서 `YOUR_API_KEY` 부분을 OpenRouter에서 발급받은 실제 API 키로 대체하세요.

### 2. Sequential Thinking MCP 서버 설치

```bash
npx -y @smithery/cli@latest install @smithery-ai/server-sequential-thinking --client cursor --key YOUR_API_KEY
```

마찬가지로 `YOUR_API_KEY` 부분을 OpenRouter API 키로 대체하세요.

## "client closed" 오류 해결 방법

MCP 서버 설치 중 또는 사용 중에 "client closed" 오류가 발생할 경우 다음 해결책을 시도해보세요:

1. **Cursor 재시작**: Cursor를 완전히 종료하고 다시 시작합니다.

2. **네트워크 연결 확인**: 인터넷 연결이 안정적인지 확인합니다.

3. **방화벽 설정 확인**: 방화벽이 MCP 서버 연결을 차단하고 있지 않은지 확인합니다.

4. **명령어 재실행**: 설치 명령어를 다시 실행합니다.

5. **CLI 옵션 추가**: 설치 명령어에 `--timeout 60000` 옵션을 추가하여 시간 초과 값을 증가시킵니다:

   ```bash
   npx -y @smithery/cli@latest install @smithery-ai/server-sequential-thinking --client cursor --key YOUR_API_KEY --timeout 60000
   ```

6. **npm 캐시 정리**:

   ```bash
   npm cache clean --force
   ```

7. **CLI 최신 버전으로 업데이트**:

   ```bash
   npm install -g @smithery/cli@latest
   ```

## 설치 확인

Cursor 설정에서 MCP 서버 목록을 확인하는 방법:

1. Cursor 열기
2. 설정 메뉴 열기 (단축키: Ctrl + ,)
3. MCP 섹션으로 이동
4. 서버 목록에서 "openrouterai"와 "server-sequential-thinking"이 녹색 점으로 표시되는지 확인
5. **중요**: 서버를 활성화하려면 "Disabled"를 클릭하여 "Enabled"로 변경해야 합니다.

## 문제 해결

만약 위의 해결책으로도 문제가 해결되지 않는다면:

1. Cursor 디버그 로그 확인:
   - Windows: `%APPDATA%\Cursor\logs`
   - macOS: `~/Library/Application Support/Cursor/logs`

2. 설치 과정에서 발생한 오류 메시지를 자세히 확인하세요.

3. 특정 문제에 대해 [Cursor Discord](https://discord.gg/cursor) 또는 [GitHub Issues](https://github.com/getcursor/cursor/issues)에서 도움을 구할 수 있습니다.