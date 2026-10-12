# 수원 문화지도 🗺️

수원문화재단 공공 API의 행사 정보를 **지도 위에서 한눈에** 보는 웹 서비스입니다.

**👉 바로 써보기: https://gwhong-dev.github.io/suwon-culture-map/**

---

## 주요 기능

| 기능 | 설명 |
|---|---|
| 지도 + 마커 | 카테고리(행사·공연·전시·축제)별 아이콘으로 행사 위치 표시 |
| 같은 장소 묶기 | 한 장소에 행사가 여러 개면 마커 1개 + 숫자 배지 |
| 검색 · 필터 | 행사 이름 검색, 카테고리, 지난 행사 보기 |
| 목록 | 시작일 순 정렬, 사진·이용료·장소·시간 요약 |
| 상세 정보 | 전체 설명 + 재단 원문 페이지 링크 |
| 찜 | 로그인 없이 이 기기·브라우저에 저장 (localStorage) |
| 모바일 | 앱처럼 동작: 떠 있는 검색창, 끌어올리는 목록(바텀시트), 마커 미리보기 카드 |

## 기술 스택

- **Frontend**: HTML · CSS · JavaScript (프레임워크 없음), Kakao Maps JavaScript API
- **배포**: GitHub Pages (정적 사이트)
- **원본 버전 Backend**: Spring Boot · JPA · MySQL · 소셜 로그인(카카오·구글·네이버)

## 구조: 원본 버전 → 배포 버전

```
[원본]  재단 API(XML) → Spring Boot → MySQL → REST API → 지도 화면
                                     └ 소셜 로그인 · 찜(DB)

[배포]  events.json(행사 데이터) ──────────────────→ 지도 화면
                                     └ 찜(브라우저 localStorage)
```

- 서버 없이 누구나 접속할 수 있게 **로그인·DB를 뺀 정적 버전**으로 배포했습니다.
- 백엔드(엔티티 설계, XML 매핑, 동기화, 소셜 로그인·계정 통합)는 원본 저장소에 있습니다.
  → [SuwonCultureMap (Spring Boot)](https://github.com/honggyeongwoo/SuwonCultureMap)

## 행사 데이터 업데이트 방법

1. 원본 Spring Boot 서버 실행 → `행사 동기화`
2. 이 폴더에서 `curl http://localhost:8080/api/events -o events.json`
3. 커밋 · 푸시 → GitHub Pages에 자동 반영

## 개발 과정

- AI(Claude)의 도움을 받아 작성했고, **직접 실행·확인한 뒤** 반영했습니다.
- 확인 항목과 발견한 문제·해결 과정: [VERIFICATION.md](VERIFICATION.md)
