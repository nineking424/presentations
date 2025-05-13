# Cursor IDE를 활용한 개발 TAT 초단축

---

## 1. 서론

### 1.1 AI의 발전과 개발자
- **LLM 기술 변혁**
    - GPT3: 장난감
    - GPT 3.5, GPT 4: 할루시네이션 급감
    - Multi Modal: 안드로이드 기반 기술
    - **AI Agent**: 요즘 대세
    - 최근 연구결과
        - *COT* (Chain of Thought)
        - *MOE* (Mixture of Expert)
- **Home lab**
    - **Compute**
        - 2 mini server (4C/8G*2)
        - 1 workstation (72C/96G)
        - 1 desktop (32C/64G/12G VRAM)
    - **Storage**: Synology NAS (24TB)
    - **Virtualization**: proxmox
    - **Infrastructure**: VM + Container (K8s)
    - **Self hosted service**: npm + vpn
    - **Development**
        - 1 mac mini
        - 1 mac book air

### 1.2 바이브 코딩이란
- "해줘"로 개발하는 시대 (like 딸깍)


### 1.3 Claude Sonnet 3.7 모델
- AI 모델의 성능적 진보 → **아~주 쓸만하다!**
- manus 사례: [까보니, 클로드](https://www.reddit.com/r/LocalLLaMA/comments/1j7n2s5/manus_turns_out_to_be_just_claude_sonnet_29_other/)

### 1.4 Benchmarks
- **SOTA (State of the Arts) Models**
- Claude 3.7 Sonnet offers state-of-the-art performance across a variety of coding, vision, and reasoning tasks.
- ![model card](https://www.anthropic.com/_next/image?url=https%3A%2F%2Fwww-cdn.anthropic.com%2Fimages%2F4zrzovbb%2Fwebsite%2F654cf6680d32858dfba9af644f8c4a5b04425af1-2600x2360.png&w=3840&q=75)
- [Claude 3.7 Sonnet and Claude Code](https://www.anthropic.com/news/claude-3-7-sonnet)

### 1.5 AI를 활용한 개발을 하며 느낀점
- 코딩이 취미지만, 코딩은 귀찮아
- 취미는 일이 아니다. 오늘 시작한 일은 오늘 끝낸다.
- AI가 코딩을 잘해? **오히려 좋아.**
- 아이디어만 있으면 되는 시대

---

## 2. Cursor 소개 및 기능

- **Cursor** - The AI Code Editor
    - VS Code 기반으로 개발된 코딩 어시스턴트 툴
    - Copilot과 가장 차별화되는 점: Codebase 전체 Scope에 대한 작업 수행
    - [Cursor 공식 사이트](https://www.cursor.com)
- **VSCode Extensions: Cline**
    - [Cline](https://cline.bot): 오픈소스, API call 방식으로 보안 이슈 없이 DS LLM 도입 가능 (모델이 받쳐줘야 함)
- **Windsurf**
    - [Windsurf Editor](https://windsurf.com/editor)
- **Cursor 주요 기능**
    - Agent, Tab, Chat ([Cursor - Features](https://www.cursor.com/features))
    - 내가 좋아하는 기능: Codebase Indexing, Agent Debugging, Accept, Terminal, auto-run mode

---

## 3. Cursor로 개발하기

### 3.1 Agent로 시작 (Codebase)
- 빈 폴더 만들고 커서 켜기
- 계획 말하고 기초 구조 잡기
- 초벌 결과물 보고 방향 잡기

### 3.2 원하는 부분만 개발 (Context)
- `@`로 파일/폴더 태그하여 코딩해줘
- 편집기 드래그 후, `Cmd+L` → 코딩해줘

### 3.3 안되면, 디버깅 (Terminal / Auto-run)
- 에러메세지 드래그 후, `Cmd+L` → 디버깅 해줘
- 자동으로 해줘
- "해줘"로 이슈 트레이스  
    [사례: DNS 이슈 해결](https://stjeong.notion.site/CoreDNS-2-1cab0623cdb2805aa540c5120d846fa8)

### 3.4 문서화
- 개요만 쓰고, 나머지 작성 요청하기
    - `instruction` 파일 생성 자동화 (SOP)
    - Kubernetes manifest 작성 자동화
- 예시: github에 업로드 하기 위한 `README.md` 파일 작성해줘. 한/영 버전 모두 작성해줘.

---

## 4. 활용 사례

### 4.1 없는 것을 만들기
- 내가 원하는 오픈소스가 없네?
    - 기존 오픈소스는 클러스터 레벨 권한이 필요
    - 네임스페이스 한정 모니터링 필요 → **kube exporter 개발**
        - [kube-state-metrics](https://github.com/kubernetes/kube-state-metrics)
        - [kubemetrics-exporter GitHub](https://github.com/nineking424/kubemetrics-exporter)

### 4.2 있는 것을 바꾸기
- **UI 개발** 잘 모르는데...  
  - Docker image loader 기능 추가 & 웹 디자인 개선
    - Before : [Docker Loader](https://docker-loader.nkmain.stjeong.com)
    - After : [Docker Loader](https://docker-loader.nks.stjeong.com)
- **Helm chart** 수정 안 해봤는데...  
    → NiFi Helm chart 2.XX 버전용으로 수정: [Helm Nifi](https://artifacthub.io/packages/helm/cetic/nifi)

### 4.3 아예 몰라도 만들기
- NiFi / Groovy script는 참고할 자료가 없네?  
    → 파싱 모듈 개발

### 4.4 더 좋게 만들기
- Parquet 압축률 테스트 및 최적화

### 4.5 문서화
- 귀찮네?  
    → git `README.md` 작성 자동화

---

## 5. 내재화 관점 활용방안

### 5.1 한계점
- Cursor의 보안정책: [Trust Center](https://trust.cursor.com/faq)
    - How does Cursor process AI requests?
    - Does Cursor use infrastructure in China?
    - How is my code data protected?
    - Do you encrypt data at rest and in transit?
- 보안성 검토가 가장 큰 벽 (혹시?)
    - VS Code + Cline extension + DS LLM + MCP plugin
- AI는 마법이 아니다. 사람에게 내 의도를 정확히 전하는 것도 쉽지 않음.
- 결과물 크로스 체크는 필수
- 반도체 도메인 지식 활용을 위한 파인튜닝/RAG 개발은 또 다른 도전과제
- 도메인 지식을 제외한 단순/반복작업의 공수 단축이 현실적 도입 가능안
- 대규모 프로젝트에도 적용 가능한지는 아직 검증되지 못함

### 5.2 S-VOC
- 코드베이스 인덱싱을 활용해, 로직 문의에 빠른 대응  
    (예: Defect FCC 로직 8인치 vs 12인치 비교분석)

### 5.3 프로그램 로직 정리
- 수백개 ETL에 대한 라인 바이 라인 설명
- 프로그램-테이블 맵핑정의서 만들어줘
- PKG 수율 데이터의 원천 테이블 찾아줘
- 쿼리 최적화 요청

### 5.4 인수인계
- 전체 프로젝트 구성 분석

### 5.5 코드 리팩토링
- C 코드를 Java 코드로 변환
- Python 코드를 C 코드로 변환
- 설비 검사 파일을 CSV 포맷으로 변환

### 5.6 SR TAT 단축
- 기존 ETL 참고 신규 ETL 개발
- Defect ETL 필수 테스트 항목 진행

### 5.7 영향도 분석
- `PART_ID`를 잘라 쓰는 ETL 찾기
- 표준화가 필요한 컬럼 찾기 (`PART_ID`, `PART_NO`, `PROD_CODE` 등)
- `EVT_FE_LOT` 테이블의 원천 DB 찾기
- `COM_CAL` 테이블의 각 컬럼별 생성 로직 정리

---

## 6. 기타

### 6.1 MCP (Model Context Protocol)
- **MCP란?** LLM 모델과 툴간 커뮤니케이션 프로토콜. Anthropic 개발. 현재 표준 프로토콜.
    - [Claude MCP Community](https://www.claudemcp.com/servers)
    - [MCP Marketplace](https://cline.bot/mcp-marketplace)

### 6.2 TaskMaster
- [TaskMaster (claude-task-master)](https://github.com/eyaltoledano/claude-task-master)
- MCP의 한 종류. AI는 장기 프로젝트에 활용이 어려움.
- 지침서를 활용한 장기 프로젝트 수행
- PRD 파일을 만들어 전달. 작은 태스크 단위로 나누어 단계별 계획 수립. 태스크별 의존성 및 진척 관리 가능
- 모델은 Claude 사용. Cursor와 연동해 활용 가능.

### 6.3 AI 모델 호출을 활용한 문서화 자동화 (개발위키)
- AI Programmer 서비스를 만든 Devin에서 개발 ([deepwiki](https://deepwiki.com))
- github repository 주소를 입력하면, 5~10분 후 개발문서 완성! (public은 무료, private은 유료)
- 코드 구조를 분석해 Diagram을 통해 모식도 시각화
- Overview ~ Development Guide 까지 완성도 높은 결과물
    - [kubemetrics-exporter](https://deepwiki.com/nineking424/kubemetrics-exporter)

### 6.4 AI Agent
- AI 모델에 R&R을 부여하고 각 AI 모델을 연결하여 구성 (keyword: langchain, google adk, n8n, Agent workflow)

### 6.5 기타 유용한 서비스
- Firebase
- NotebookLM
- OpenRouter
- Groq
- [위키독스: 파이썬으로 배우는 알고리즘 트레이딩](https://wikidocs.net/book/14473)
- [인터뷰 코더](https://maily.so/thesync/posts/d5ryll34o1w)

![스크린샷 2025-05-14 오전 1 40 09](https://github.com/user-attachments/assets/c9311154-2391-467f-bea2-58a4fe17b6e3)
