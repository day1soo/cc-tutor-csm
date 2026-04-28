# cc-tutor-csm

B2B CSM(Customer Success Manager)팀을 위한 Claude Code 학습 튜터.
하루 집중 워크숍(4~8h)으로 자기 반복 업무 1개를 스킬로 자동화하는 것이 목표입니다.

## 빠른 시작

### 가장 쉬운 방법 (한 줄 부탁)

Claude Code를 아무 폴더에서 실행한 뒤, 아래처럼 부탁하세요:

```
https://github.com/day1soo/cc-tutor-csm 이거 학습하고 싶어. 설치해줘
```

Claude가 알아서 레포를 받아오고, 그 폴더에서 다시 Claude Code를 열라고 안내합니다.
열고 나면 `/cc-tutor-csm` 또는 "학습 시작" 이라고 입력하면 튜터가 시작돼요.

### 직접 명령어로 설치

```bash
# 1. 레포 클론
git clone https://github.com/day1soo/cc-tutor-csm.git
cd cc-tutor-csm

# 2. Claude Code 실행
claude

# 3. 튜터 시작
/cc-tutor-csm
```

## 커리큘럼 (하루 워크숍)

| 시간 | 모듈 | 내용 |
|------|------|------|
| 10:00 | M1 환경 세팅 | Claude Code 기초 + CLAUDE.md 작성 |
| 10:45 | M2 데이터 분석 | 기업리스트 필터링 + 리포트 자동 생성 |
| 12:15 | 점심 | |
| 13:15 | M3 Slack 연동 | Slack MCP + 메시지 검색·요약·draft |
| 14:30 | M4 스킬 제작 | 자기 업무 1개 스킬화 |
| 16:30 | 회고 | 시연 + 다음 단계 안내 |

## 스킬 옵션 (M4)

| 옵션 | 스킬 | 난이도 |
|------|------|--------|
| A | /신규딜세팅 | ⭐ |
| B | /월간리포트 | ⭐⭐ |
| C | /기업현황 | ⭐⭐ |

## 폴더 구조

```
cc-tutor-csm/
├── .claude/skills/cc-tutor-csm/   # 튜터 스킬 엔진
│   ├── SKILL.md                    # 메인 동작 정의
│   └── references/                 # 모듈별 교안
├── samples/                        # 샘플 데이터 (익명화)
├── my-data/                        # 실제 데이터 (본인용)
├── CLAUDE.md                       # 프로젝트 규칙
└── README.md
```

## 사전 준비 (참가자)

- [ ] Claude Code 설치
- [ ] Claude 계정 로그인
- [ ] 이 레포 클론
- [ ] (선택) `my-data/`에 실제 데이터 넣기
