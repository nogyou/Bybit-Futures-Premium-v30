# BYBIT FUTURES PREMIUM v3.0 alpha1 (새 Android 앱)

기존 v2.7/v2.9와 별도 설치: `com.bybit.premiumv3`. GitHub Actions가 `app-debug.apk` 빌드.

## 실제 구현
- Bybit 공개 REST API: USDT 무기한 캔들 200개 및 현재가 (15초 간격 요청)
- 10개 종목 선택, 1/3/5/15/60/240분·일봉, 전체 새 가로 UI, 캔들 차트
- EMA20/50, RSI14, ATR14, 40봉 고저점, 거래량을 사용한 **조건부 LONG/SHORT 가격 후보**, TP1/TP2/SL, 손절률, R:R
- 메인 차트에 진입/TP1/SL/현재가 수평선. 가격 도달 시 반등/거래량 확인 여부 표시.

## 반드시 알아야 할 한계
- **alpha1, 미검증**. 실전 거래 또는 투자 결정에 단독 사용 금지. 가상매매로 충분히 검증해야 함.
- LONG/SHORT 가격은 단순 ATR·고저점 휴리스틱이며 AI 학습모델/검증된 예측 시스템이 아님.
- OI, 펀딩비, 호가, 뉴스, WebSocket, 월봉, 자동매매, 백테스트, 신호 저장 및 체결 후 포지션 관리는 **아직 구현되지 않음**. 그래서 항상 WAIT 판단만 표시함.
- 네트워크 오류·Bybit 지역별 접속 제한 가능. API 키 불필요. REST 폴링이며 진정한 틱 단위 실시간 아님.
- 캔들 최신 봉은 미완성일 수 있음. 슬리피지·수수료·레버리지 미반영.

## 빌드
1. 이 ZIP을 새 GitHub 저장소에 압축 해제 후 업로드
2. Actions → Build Bybit Futures APK → 성공한 run → Artifacts → Bybit-Futures-v30-alpha1-debug-APK
3. ZIP 압축 해제 후 app-debug.apk 설치

### 다음 구현 우선순위
WebSocket 및 신호 신선도 → 독립 지표 다중 확인 → OI/펀딩/호가 → 뉴스 → 백테스트/모의매매 → 신호 검증 → 실제 진입 권고 상태
