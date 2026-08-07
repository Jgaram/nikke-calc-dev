# archive — 동결된 코드

**여기 있는 것은 고치지 않는다.** 계산기 코드가 바뀌어도 맞춰 주지 않고,
`doclint`도 훑지 않는다. 남겨 둔 이유는 참고와 복원 가능성뿐이다.

## Streamlit UI (2026-08-07 개발 종료)

| 파일 | 내용 |
|---|---|
| `app.py` | 진입점. `streamlit run app.py` |
| `run.bat` | 더블클릭 실행용 |
| `ui/` | 화면 모듈 (팀 편성·육성·버프 타임라인·히트 추적) |
| `UI.md` | 화면 구성·표시 규칙 문서 (동결) |

**지금 이 상태로는 돌지 않는다.** 저장소 루트에서 옮겨 왔으므로 임포트 경로가 맞지 않고,
`data/control_defaults.json`(UI 전용 파일)은 `data/char_defaults.json`으로 흡수되며 삭제됐다.
되살리려면 파일을 루트로 되돌리고 컨트롤 기본값 로더를 새 파일에 맞춰 고쳐야 한다.

구현 확인은 이제 `python -m context.sim`(단발) · `python -m context.snapshot`(회귀) ·
`/report`(비교 보고서)로 한다. 세 도구 모두 `context/spec.py`의 같은 기본 스펙을 쓴다.
