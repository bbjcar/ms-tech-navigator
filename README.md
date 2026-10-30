# MS Tech Navigator

Microsoft 공식 문서와 공개 로드맵을 기반으로 기술 학습과
질의응답을 지원하는 Microsoft 365 Copilot 선언형 에이전트입니다.

Microsoft 365 Agents Toolkit으로 개발했으며,
MCP 서버와 기본 제공 기능을 조합한 에이전트 설계를 실습합니다.

> 개인 개발 프로젝트이며 Microsoft 공식 제품이 아닙니다.

## 주요 기능

- Microsoft Learn 공식 문서 및 코드 샘플 검색
- Microsoft 365 로드맵 및 Azure 업데이트 조회
- 공식 커뮤니티와 블로그를 활용한 보조 검색
- Microsoft 기술 개념 설명과 학습 퀴즈
- 표·차트·파일 생성 및 개념 설명용 이미지 생성
- 설정과 사용자 권한에 따른 Microsoft 365 업무 정보 참조

## 구성

사용자 질문
→ Microsoft 365 Copilot의 관리형 오케스트레이션
→ 지침과 도구 설명에 따라 검색·도구 실행
→ 근거를 바탕으로 답변 생성

### 연결한 MCP 서버

- Microsoft Learn MCP
- Microsoft Release Communications MCP

### 기본 제공 기능

- WebSearch
- OneDriveAndSharePoint
- Email
- TeamsMessages
- Meetings
- CodeInterpreter
- GraphicArt

실제 사용 가능 범위는 배포 환경, 라이선스, 조직 정책 및
사용자 권한에 따라 달라질 수 있습니다.

## 설계 포인트

- 개념·설정·API 질문에는 공식 문서를 우선 활용합니다.
- 출시 상태와 사용 방법을 구분해 확인하도록 지침을 구성합니다.
- 커뮤니티 의견과 공식 문서의 근거를 구분합니다.
- 사내 정보가 외부 검색어에 포함되지 않도록 지침을 구성합니다.
- 환경별 값은 env 파일로 분리합니다.

지침은 모델의 행동을 유도하는 설정이며,
보안 정책이나 접근 권한 통제를 대체하지 않습니다.

## 주요 파일

- appPackage/manifest.json: 앱 정보와 에이전트 연결
- appPackage/agent.json: 지침, 기능, 플러그인 연결
- appPackage/instruction.txt: 에이전트 행동 지침
- appPackage/ai-plugin*.json: MCP 플러그인 구성
- appPackage/mcp-tools*.json: 참조하는 MCP 도구 정의
- m365agents.yml: 수명 주기 작업 정의
- env/.env.dev.sample: 환경 설정 예시
- PRIVACY.md: 개인정보 및 데이터 처리 안내
- TERMS.md: 이용 안내

파일명과 구성은 프로젝트 버전에 따라 달라질 수 있습니다.

## 실행 및 테스트

1. VS Code에서 프로젝트를 엽니다.
2. Microsoft 365 Agents Toolkit을 설치하고 계정에 로그인합니다.
3. env/.env.dev.sample을 복사해 env/.env.dev를 만듭니다.
4. 환경 변수와 앱 정보를 본인의 환경에 맞게 설정합니다.
5. m365agents.yml의 환경 폴더 설정을 확인합니다.
6. Lifecycle에서 Provision을 실행합니다.
7. 생성된 패키지와 에이전트 동작을 확인합니다.

조직 게시에는 별도의 관리자 승인과 배포 설정이 필요할 수 있습니다.

## 테스트 질문 예시

- Copilot Studio에서 MCP 서버를 연결하는 방법을 알려줘.
- Teams의 공개 로드맵에서 출시 중인 기능을 찾아줘.
- 신규 기능의 출시 상태와 설정 방법을 함께 설명해줘.
- Microsoft Entra ID 기초 퀴즈를 만들어줘.
- 조회한 로드맵을 표와 이미지 파일로 정리해줘.

## 보안 및 공개 범위

이 저장소에는 실제 인증 정보와 조직별 환경 설정을 포함하지 않습니다.

- Secret, 토큰, 인증서 및 민감한 환경 파일은 커밋하지 않습니다.
- 생성된 앱 패키지에도 환경값이 포함될 수 있으므로 공개 전 검토합니다.
- 공개 예시와 조직 배포본의 설정은 다를 수 있습니다.
- 문의나 오류 보고에 개인정보와 사내 정보를 포함하지 마세요.

## 한계

- AI 답변에는 오류나 누락이 포함될 수 있습니다.
- 로드맵과 출시 일정은 변경될 수 있습니다.
- 검색 결과가 모든 관련 자료를 포함한다고 보장하지 않습니다.
- 실제 설정 변경과 코드 실행 전에는 공식 문서를 확인해야 합니다.
- 외부 MCP 및 플랫폼 변경에 따라 동작이 달라질 수 있습니다.

## 향후 계획

- 대표 질문 기반 회귀 테스트 정리
- 도구 선택과 출처 정확도 평가
- 다른 에이전트 구현 방식과 비교
- 민감 정보를 제거한 실행 화면 추가