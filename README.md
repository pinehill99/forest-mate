# 숲길동무 (ForestMate)

「2026년 산림 공공데이터·AI 활용 창업경진대회」 **제품 및 서비스 개발 부문** 출품 패키지.
산림 공공데이터 10종과 AI를 융합한 **국민 산행 안전 플랫폼** — 맞춤 추천 → 위험 경고 → 조난 자동 감지 → B2G 관제.

> 접수 마감: **2026. 6. 19.(금) 18:00**, 산림청 누리집 온라인 접수

## 폴더 구성

```
forest-mate/
├── app/                  # 동작하는 프로토타입
│   ├── index.html        #   모바일 앱 (홈·산행·AI동무·SOS·마이 5개 화면, PWA)
│   ├── dashboard.html    #   B2G 관제 웹 대시보드
│   ├── manifest.json     #   PWA 매니페스트 (홈화면 설치)
│   └── sw.js             #   오프라인 서비스워커
├── assets/               # 앱 스크린샷 + 제안서/PPT용 차트·다이어그램 PNG
├── deliverables/
│   ├── 숲길동무_기획서_제품서비스개발부문.docx   # 제안서 (HWP 양식 항목 그대로)
│   └── 숲길동무_발표자료.pptx                    # 2차 발표평가용 15장
├── make_charts.py        # 차트·다이어그램 생성 스크립트 (matplotlib)
├── make_docx.js          # 제안서 생성 스크립트 (docx-js)
└── make_pptx.js          # 발표자료 생성 스크립트 (pptxgenjs)
```

## 프로토타입 실행

```bash
cd forest-mate/app && python3 -m http.server 5181
# 모바일 앱:   http://localhost:5181/index.html   (브라우저 폭을 좁히거나 모바일로 접속)
# 관제 대시보드: http://localhost:5181/dashboard.html
```

- 탭 직접 열기: `index.html?t=trail` (home / trail / ai / sos / my)
- SOS 버튼 1.5초 길게 누르면 신고 시연 알림이 뜹니다.

## 스토어 등록(접수 전 필수)

기획서 ‘등록 정보’ 칸에는 실제 URL이 필요합니다. 빠른 경로:

1. **웹**: `app/` 폴더를 Vercel/Netlify/GitHub Pages에 그대로 업로드 → 웹 URL 확보 (PWA라 설치도 동작).
2. **구글**: [PWABuilder](https://pwabuilder.com) 또는 Bubblewrap으로 TWA 패키징 → Play Console 비공개 테스트 트랙 URL.
3. **애플**: Capacitor로 래핑(`npx cap add ios`) → TestFlight 공개 링크.
4. DOCX의 노란색 표시 칸(팀명·URL·팀 실적)을 교체하고, 본문을 공고 HWP 양식에 옮겨 제출.

## 산출물 재생성

```bash
python3 make_charts.py                      # 차트 PNG
NODE_PATH=$(npm root -g) node make_docx.js  # 제안서 DOCX
NODE_PATH=$(npm root -g) node make_pptx.js  # 발표 PPTX
```

## 데이터 출처 (기획서 2장에 URL 명기)

산림청 등산로 공간정보 · 국립산림과학원 산불위험예보/산악기상관측망 · 산사태정보시스템 · 국립수목원 국가생물종지식정보 · 한국산림복지진흥원 숲나들e · 산림빅데이터 거래소 · 소방청 산악사고 현황 · 행정안전부 국가지점번호 · 기상청 단기예보
