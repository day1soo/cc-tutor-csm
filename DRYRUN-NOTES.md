# 드라이런 노트

> 2026-04-22, 수정 착수 전 CSM 초보 관점 시뮬레이션

---

## M1 실습 결과

### 실습 1 (폴더 구조 확인) — OK
- 프롬프트 정상 동작. 3줄.
- 관찰: 성공 기준의 파일 목록은 명시적이라 이해 가능.

### 실습 2 Step 1 (samples/ 목록 훑기) — 🔴 **성공 기준 오류**
- 실제 `samples/` 파일 수: **6개** (README-samples.md, data-extraction-sop.md, enterprise-list-sample.csv, new-deal-message-sample.txt, operation-checklist-sample.csv, report-rawdata-sample.csv)
- 현재 성공 기준: "5개 파일 — CSV 3개 + MD 1개 + TXT 1개"
- 실제 분포: **CSV 3 / MD 2 / TXT 1**
- → 수정 필요

### 실습 2 Step 2 (수료기준 교차 검색) — OK
- Grep 정상. 3개 파일에서 "수료기준" 발견 (operation-checklist / new-deal-message / enterprise-list)

### 실습 3 (CLAUDE.md append) — 관찰
- 프롬프트가 17줄 짜리 긴 코드 블록. 3줄 기준 초과.
- 대안: CLAUDE.md에 이미 CSM 운영 규칙이 있으니, "본인 규칙 1줄 추가해보세요" + 예시 링크 형태로 변경
- 혹은 블록 전체를 **학습자가 고를 수 있는 템플릿**으로 별도 박스에 두고 EXECUTE 본문은 "아래 템플릿 중 1~2 섹션 골라 CLAUDE.md에 append 해달라고 해보세요" 한 줄로 축약

### 실습 4 (A전자 리포트 초안) — 프롬프트 길이 초과
- 현재 5줄. 특히 "CLAUDE.md 어떤 규칙이 반영됐는지 표로 정리해줘" 뒷부분이 자가 체크를 뺏음
- 수정: 리포트 생성 2줄 + 자가 체크박스 4칸으로 분리

---

## M2 실습 결과

### 실습 1 (기업리스트 요약) — 🟡 **프롬프트 6줄**
- 데이터 결과는 정상: 총 10개 / ongoing 8 : closed 2 / High 4 / Medium 2 / Low 4
- 축약 제안: `samples/enterprise-list-sample.csv 읽고 총 기업 수 / ongoing:closed 비율 / 운영난이도 분포 요약해줘` (1줄)

### 실습 5 (Plan 모드 리포트) — OK
- 현재 2줄. 길이 OK.

---

## M3 (현재 Google Drive 버전) — 스킵, 전면 교체 예정

---

## M4 (/신규딜세팅 트리거) — 시뮬 한계
- 스킬이 `.claude/skills/신규딜세팅/SKILL.md` 경로에 등록돼야 트리거
- 현재 워크숍 구조에서 이 경로 안내가 전혀 없음 → **치명적 확정**

---

## Slack MCP 확인 결과

**사용 가능 도구 (auth 전):**
- `mcp__claude_ai_Slack__authenticate` — OAuth 시작, authorization URL 반환
- `mcp__claude_ai_Slack__complete_authentication` — 콜백 URL 전달로 완료

**auth 플로우 (4단계):**
1. Claude에게 "Slack 연결하고 싶어" → authenticate 호출 → authorization URL 응답
2. 학습자가 URL을 브라우저에서 연다 → Slack 로그인 + 워크스페이스 승인
3. 브라우저가 `http://localhost:<port>/callback?code=...&state=...` 로 리디렉트 (페이지는 실패해도 주소창 URL이 유효)
4. 학습자가 주소창 URL 복사 → Claude에게 붙여넣기 → complete_authentication 호출

**auth 후:** 실제 메시지 검색/읽기/작성 도구가 자동 추가됨 (이름은 auth 후 확인)

**CSM 실습 설계 방향:**
- 구체 도구명 대신 **자연어 프롬프트**로 감싸기: "Slack에서 최근 7일 '신규딜' 포함 메시지 찾아줘"
- 실습 1 = auth 플로우 체험 (한 번에 1화면 단위)
- 실습 2~4 = 검색·요약·draft 작성

**사전 준비 영향:** 개인 Slack 계정으로 로그인만. 퍼실리테이터 세팅 0. ✅

---

## 종합 발견사항 (계획 보강)

### 새로 추가할 이슈
- **M1 실습 2 Step 1 성공 기준 오류** (5개 → 6개 파일)
- **M1 실습 3 프롬프트 과도한 길이** (17줄 코드 블록 → 축약 또는 별도 템플릿 박스)
- **M1 실습 3 본문 프롬프트 축약** (EXECUTE엔 "템플릿 중 1~2개 골라 append 해달라고 해보세요" 1줄)
- **Slack auth는 4단계 플로우** — "🔌 Slack 켜기" 박스를 실습 0로 명시. 스크린샷/도식 포함 고려

### 계획 수정사항
- M3 실습 1이 auth 플로우 자체가 됨 → 실습 1 = "Slack 연결", 실습 2 = 검색, 실습 3 = 요약, 실습 4 = draft
- glossary.md의 MCP 동작 행은 auth 완료 후에 실제 도구 이름 확인하고 업데이트 (TBD 주석 삽입)

### 리스크
- Slack 워크스페이스 접근 권한이 회사마다 다름 — CSM 각자 본인 워크스페이스 "앱 추가" 권한 있어야 함. troubleshooting.md에 "회사 정책상 앱 추가 막힌 경우 → 퍼실리테이터 본인 테스트 워크스페이스로 대체"
