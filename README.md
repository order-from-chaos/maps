# maps

제주 / 여행 커스텀 지도 PWA. Leaflet + OSM 타일 + 네이티브 앱 URL scheme 점프.

## 구조

- `index.html` — Leaflet 렌더러
- `pins.json` — 핀 데이터 (lat/lng/category/name/note)
- `manifest.json` — PWA 메타
- `sw.js` — service worker (app shell 캐시)
- `icon.png` — 홈 아이콘

## 핀 업데이트

`pins.json` 편집 후 push. GitHub Pages가 자동 배포.

## iOS 사용

1. Safari로 `https://order-from-chaos.github.io/maps/` 접속
2. 공유 → 홈 화면에 추가
3. 아이콘 탭 → standalone 앱처럼 실행
4. 핀 탭 → 팝업 → [네이버 지도 열기] / [카카오맵 열기]

## Category 색상

| category | color |
|---|---|
| anchor | blue |
| transit | purple |
| scenic | green |
| food | orange |
| cafe | pink |
| stay | yellow |
| other | gray |

## 제약 (2026-04-13 확인)

- URL scheme은 단일 좌표 이동만 — 일괄 import scheme 없음
- Naver/Kakao/Google 즐겨찾기 쓰기 API 없음
- OSM 타일은 한국 POI 약함 — 길찾기는 Naver/Kakao 네이티브에 위임
- iOS PWA offline 캐시는 7일 미사용 시 eviction 가능

## Related

- Parent: `order-from-chaos/GHOST` Issue #20
