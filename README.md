# hosrank-batch

[병원체크(hoscheck.com)](https://hoscheck.com)의 공공데이터 수집 배치를 **실행만** 하는 저장소입니다.

- 수집 코드와 웹사이트 코드는 비공개 저장소(`univblind/hosrank`)에 있습니다. 여기에는 언제 무엇을 실행할지(GitHub Actions 설정)만 있습니다.
- 실행할 때 배치용 열쇠(`HOSRANK_DEPLOY_KEY`)로 비공개 저장소 코드를 받아 와서 돌립니다.
- 공개 저장소라 GitHub Actions 실행 시간이 무료입니다.

## 배치

| 설정 | 하는 일 | 언제 |
|---|---|---|
| `ingest.yml` | 병원 기본정보·상세·평가등급·점수, 응급실, 약국, 진료시간 보완, 건강검진기관, 실손24, 의원 많이 진료한 질병, **병원별 비급여(심평원 누리집)**, 검색엔진 알림, 사이트 화면 갱신 | 매일 03:17 KST (보조 05:47) |
| `holiday.yml` | 설·추석 비상진료기관 | 명절 21일 전부터 하루 두 번 |

실행 결과는 [Actions](../../actions) 화면 맨 위에 한국어 요약으로 남습니다.

## 필요한 비밀값 (Settings → Secrets and variables → Actions)

| 이름 | 내용 |
|---|---|
| `HOSRANK_DEPLOY_KEY` | `univblind/hosrank` 배포 열쇠의 비밀 키 (쓰기 허용: 데이터 기준 월 커밋) |
| `SUPABASE_URL` | Supabase 프로젝트 주소 |
| `SUPABASE_SERVICE_ROLE_KEY` | Supabase 서비스 키 |
| `DATA_GO_KR_KEY` | 공공데이터포털 인증키 |
| `REVALIDATE_SECRET` | 사이트 화면 갱신 요청 키 (Vercel 환경변수와 같은 값) |

출처: 건강보험심사평가원, 국립중앙의료원, 국민건강보험공단, 보험개발원, 한국천문연구원 공공데이터.
