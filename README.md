# maps

Personal travel map PWA — Leaflet + OSM + Naver/Kakao URL scheme jump.

## 현재 포지션 (2026-04-14)

이 PWA는 **주력에서 보조로 전환됨**.

- **주력 뷰어:** Obsidian Map View 플러그인 (JH vault 내부)
  - 2GB offline tile, Auto-add GPS, vault 통합
  - Custom "Open In" 으로 카카오/네이버 네이티브 점프
- **이 PWA의 역할:**
  - 웹 공유용 (타인에게 핀 리스트 보여줄 때)
  - Obsidian 접근 불가 환경의 백업 뷰어
  - iOS PWA URL scheme 실험 레퍼런스 (T2 검증)

## 구조

- `index.html` — Leaflet 렌더러
- `pins.json` — 핀 데이터 (lat/lng/category/name/note)
- `manifest.json` — PWA 메타
- `sw.js` — service worker (app shell 캐시)
- `icon.png` — 홈 아이콘

## 핀 업데이트

`pins.json` 편집 후 push. GitHub Pages 자동 배포.

## iOS 사용 (웹 공유 받은 사람 기준)

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
- iOS PWA offline 캐시는 7일 미사용 시 eviction 가능 (Obsidian Map View 대비 약점)

## 주력 시스템 문서

JH vault 내부 `Projects/Reloc/jeju/travel-map/`:
- `_plan.md` — Phase 별 계획
- `_settings.md` — Map View 설정 + 카카오/네이버 scheme 전체
- `_setup-requests.md` — JH 셋업 체크리스트
- `_field-notes.md` — 현장 피드백

## Related

- Parent: `order-from-chaos/GHOST` Issue #20 (본 트랙)
- Issue #21 (Reloc 폴더 구조 개편, 장기)
