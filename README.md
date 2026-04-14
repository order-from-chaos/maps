# maps

Personal travel map PWA — Leaflet + OSM + Naver/Kakao URL scheme jump.

## 현재 포지션 (2026-04-15)

이 PWA는 **보조 뷰어** 위치로 운영 중. 실제 워크플로우는 Obsidian Map View에서.

- **주력:** Obsidian Map View (vault 내 `Projects/Reloc/travel-map/`)
  - 2GB offline tile, Auto-add GPS, vault 통합
  - Custom "Open In" 4종 (카카오 검색/좌표/로드뷰, 네이버)
  - 7 카테고리 색상/아이콘 Display Rules
  - Kakao Local API 연동 skill (`.claude/skills/travel-map/`) — chat으로 핀 자동 생성
- **이 PWA의 역할:**
  - 웹 공유용 (Obsidian 없는 사람에게 링크 전달)
  - Obsidian 접근 불가 환경의 백업 뷰어
  - iOS PWA URL scheme 실험 레퍼런스 (T1/T2 검증)

## 현재 vault 핀 (2026-04-15 제주 29핀)

| 파일 | 핀 수 | 태그 |
|---|---|---|
| `.prv-stay.md` | 1 | pin/stay (private) |
| `jeju-transit.md` | 2 | pin/transit |
| `jeju-scenic.md` | 9 | pin/scenic |
| `jeju-imjang-deepresearch.md` | 6 | pin/imjang/deepresearch |
| `jeju-imjang-daangn.md` | 11 | pin/imjang/daangn |

이 PWA의 `pins.json`은 구 샘플 5개 (제주 기본 명소). 실제 핀은 vault가 single source of truth.

## PWA 구조

- `index.html` — Leaflet 렌더러
- `pins.json` — 핀 데이터 (샘플)
- `manifest.json` — PWA 메타
- `sw.js` — service worker (app shell 캐시)
- `icon.png` — 홈 아이콘

## 핀 업데이트

`pins.json` 편집 후 push. GitHub Pages 자동 배포.

향후 vault → PWA 자동 export 스크립트 가능 (Phase 4.5+).

## iOS 사용 (웹 공유 받은 사람 기준)

1. Safari로 `https://order-from-chaos.github.io/maps/` 접속
2. 공유 → 홈 화면에 추가
3. 아이콘 탭 → standalone 앱처럼 실행
4. 핀 탭 → 팝업 → [네이버 지도 열기] / [카카오맵 열기]

## Category 색상 (PWA 내부 pins.json)

| category | color |
|---|---|
| anchor | blue |
| transit | purple |
| scenic | green |
| food | orange |
| cafe | pink |
| stay | yellow |
| other | gray |

(vault Map View의 태그 체계와 일부 다름 — PWA는 단순 view용)

## vault Map View 태그 체계

| 태그 | 색 | 아이콘 |
|---|---|---|
| `pin/food` | orange | utensils |
| `pin/friend` | pink | user-group |
| `pin/imjang/deepresearch` | red | house |
| `pin/imjang/daangn` | cadetblue | key |
| `pin/scenic` | green | mountain |
| `pin/stay` | yellow | bed |
| `pin/transit` | purple | plane |

## 제약 (2026-04-13 확인)

- URL scheme은 단일 좌표 이동만 — 일괄 import scheme 없음
- Naver/Kakao/Google 즐겨찾기 쓰기 API 없음
- OSM 타일은 한국 POI 약함 — 길찾기는 Naver/Kakao 네이티브에 위임
- iOS PWA offline 캐시는 7일 미사용 시 eviction 가능 (Obsidian Map View 대비 약점)

## 주력 시스템 문서

JH vault 내부 `Projects/Reloc/travel-map/`:
- `_plan.md` — Phase 별 계획
- `_settings.md` — Map View 설정 + 카카오/네이버 scheme 전체
- `_setup-requests.md` — JH 셋업 체크리스트
- `_field-notes.md` — 현장 피드백 (Phase 3)
- `_skill-draft.md` / `_shortcut-design.md` — Phase 1/4 설계 노트
- `pins/jeju/*.md` — 실제 핀 (테마별 파일)

## Related

- Parent: `order-from-chaos/GHOST` Issue #20 (본 트랙)
- Issue #21 (Reloc 폴더 구조 개편, 장기)
- Issue #22 (Relay UX), #23 (Edit allowlist) — 부수 UX 개선
