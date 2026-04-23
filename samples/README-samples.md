# 샘플 데이터 안내

이 폴더에는 cc-tutor-csm 학습용 샘플 데이터가 들어있습니다.
**실제 기업/수강생 정보가 아닌 익명화된 가상 데이터**입니다.

## 파일 목록

| 파일 | 사용 모듈 | 설명 |
|------|----------|------|
| `enterprise-list-sample.csv` | M2, M4 | 기업 운영 리스트 (10개 기업, 익명화) |
| `report-rawdata-sample.csv` | M2, M4 | 월간 리포트 원본 데이터 (30건) |
| `new-deal-message-sample.txt` | M4 | 신규딜 입과 요청 슬랙 메시지 예시 |
| `data-extraction-sop.md` | M2 | 리포트 데이터 추출 수작업 SOP |
| `operation-checklist-sample.csv` | M2 | 운영 시기별 체크리스트 (14개 항목) |

## 실제 데이터로 실습하려면

`my-data/` 폴더에 본인의 실제 데이터를 넣으세요.
- 기업리스트 → `my-data/enterprise-list.csv`
- 리포트 raw데이터 → `my-data/report-rawdata.csv`

각 모듈은 `my-data/`를 먼저 확인하고, 없으면 `samples/`를 사용합니다.
