# element-atelier-img

[element-atelier](https://github.com/polos0117/element-atelier) 의 그림 저장소. 코드 저장소가 무거워지지 않게 그림은 여기 둔다 — Pages 로 `https://polos0117.github.io/element-atelier-img/img/<파일>` 에서 읽는다.

## 자리

```
img/<카드>_<세계>_<화풍>_f.webp       세계 그림. 1024×1536 (2:3). 세계는 fantasy · steampunk · mecha
img/<카드>_<화풍>_f_casualN.webp      일상컷 N — 세계를 안 탄다
img/<카드>_<화풍>_f_extraN.webp       특별컷 N (선택)
img/thumb/<같은 이름>                 목록용(긴 변 512, webp 72). 워크플로가 만든다
records/<카드>/<세계>-ui.json         어떻게 만들었나 — 생성기의 "기록 내보내기" JSON 그대로
records/<카드>/casualN-ui.json        일상컷의 기록
```

파일 이름이 곧 등록 정보다. 카드 열쇠는 코드 저장소 `data/element-design.json` 의 세 층을 붙임표(-)로 이은 것이고, 밑줄(_)은 칸 사이에만 쓴다.

| 층 | 열쇠 | 보기 |
|---|---|---|
| 근본(나라) | `<나라>` | `fe_fantasy_game_keyart_f.webp` |
| 가문주 | `<나라>-<가문>` | `fe-steel_steampunk_game_keyart_f.webp` |
| 주민 | `<나라>-<가문>-<주민>` | `fe-steel-sword_mecha_game_keyart_f.webp` · `h-water-bottle_game_keyart_f_casual1.webp` |

화풍 열쇠는 코드 저장소 `data/style.json` 의 `styles`(지금은 `game_keyart`). 성별 표시 `_f` 는 반드시 붙인다. 개방(`_open`)도 연출컷(`action`)도 없다 — 카드 하나에 세계 셋과 일상컷이 전부다. 뒤에서부터 성별 → 화풍 → 세계를 벗기고 남는 것이 카드 열쇠여야 하고, 아니면 등록기가 "그런 카드가 없다" 로 서서 아무것도 적지 않는다.

원본 PNG 는 올리지 않는다 — 기록에 sha256 만 적는다. 그림을 덮어쓰지 않는다 — 바꿔 달라고 한 그림만 바꾸고 앞 그림의 sha256 을 `replacement.json` 에 남긴다.

## 올린 뒤에 할 일

없다. `img/` 에 webp 를 올리면 `썸네일` 워크플로가 `img/thumb/` 를 만들어 되커밋하고, 코드 저장소의 `그림 등록` 을 깨워 `data/img.json` 에 적게 한다. 깨우려면 이 저장소의 Actions 비밀 `CODE_REPO_TOKEN`(Fine-grained token, 저장소 element-atelier 하나, Contents: Read and write)이 있어야 한다 — 없으면 코드 저장소가 한 시간마다 스스로 돈다. 화면(도감·생성기)은 `data/img.json` 에 적힌 것만 그린다.
