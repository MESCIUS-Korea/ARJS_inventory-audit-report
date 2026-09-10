# 재고조사 보고서 템플릿 (Inventory Count Report Template)

**ActiveReportsJS Designer**로 제작된 재고조사 보고서(Inventory Count Report) 샘플 보고서 템플릿입니다.
`.rdlx-json` 형식으로 제공되며, 기업에서 보유 중인 제품·자재의 재고량을 파악하고 실제 재고와 장부상 재고를 비교하는 실무 문서 양식을 기반으로 설계되었습니다.

> 재고조사 보고서는 기업에서 보유 중인 제품이나 자재의 현재 재고량을 파악하기 위한 문서로, 실제 재고와 장부상의 재고를 비교하여 오차를 확인하고 재고를 보다 효율적으로 관리할 수 있게 해줍니다.

---

## 📌 주요 특징

- **고정 페이지 레이아웃(Fixed Page Layout)** + **가로 방향(Landscape)** 설정으로, 데이터가 많은 표를 한 페이지에 효과적으로 표시
- 테이블 행의 **표시 여부(행 숨김) 속성**에 표현식을 적용해, 특정 조건(과부족 발생 등)에 부합하는 행만 선별적으로 표시
- 이월재고·입고/출고 수량·반품 데이터를 기반으로 **현재고 및 과부족 수량을 수식으로 자동 계산**
- 과부족 수량에 따라 **비고란에 "대량 과부족 발생" / "과부족 발생" 등 안내 문구를 자동 표시**
- 과부족 품목만 별도로 정리한 **상세 테이블**에서 과부족원인과 처리방안을 자동 산출하여 표시
- 품목별 재고 현황을 **세로 막대 차트 + 선 차트**로 결합해 시각화

---

## 🗂️ 포함된 재고조사 보고서 항목

| 구분 | 항목 |
|---|---|
| 보고서 정보 | 연도, 시작일, 종료일, 부서, 직위, 보고자 |
| 재고 정보 | 품목, 규격, 단위, 이월재고, 입고 수량, 입고 반품, 출고 수량, 출고 반품, 적정재고 |
| 산출 정보 | 현재고, 과부족, 비고 |

---

## 📄 보고서 구성 특징

| 구성 요소 | 설명 |
|---|---|
| 고정 페이지 레이아웃 + 가로 방향 | 매 페이지 동일한 양식 유지, 데이터가 많은 표에 적합한 가로 보기 적용 |
| 재고 조사 현황 테이블 | 이월재고·입출고·반품 데이터를 기반으로 현재고와 과부족을 자동 계산해 표시 |
| 과부족 품목 상세 테이블 | 표현식으로 과부족 품목만 필터링하여 원인과 처리방안을 함께 표시 |
| 재고 시각화 차트 | 세로 막대 차트와 선 차트를 결합해 품목별 재고 현황을 시각적으로 표현 |

### 주요 데이터 표현식 예시

```plaintext
// 현재고 계산
{beginning_inventory + incoming_quantity - incoming_returns - outgoing_quantity + outgoing_returns}

// 과부족 계산
{optimal_inventory - (beginning_inventory + incoming_quantity - incoming_returns - outgoing_quantity + outgoing_returns)}

// 비고 자동 표시
{IIF(과부족값 < -50, "대량 과부족 발생", IIF(과부족값 < 0, "과부족 발생"))}
```

---

## 🚀 사용 방법

ActiveReportsJS Viewer를 이용하여 아래와 같이 보고서를 불러올 수 있습니다.

```javascript
viewer.open("재고조사 보고서.rdlx-json");
```

템플릿은 **ActiveReportsJS Designer**에서 열어 자유롭게 커스터마이징(항목 추가/수정, 레이아웃 변경, 데이터 소스 연결 등)하실 수 있습니다.

---

## 🛠️ 사용 기술

- [ActiveReportsJS](https://www.mescius.co.kr/activereportsjs) Designer
- `.rdlx-json` 리포트 포맷
- 고정 페이지 레이아웃(Fixed Page Layout), 가로 방향(Landscape)
- 표현식(IIF, Sum 함수), 행 숨김 조건부 표시
- 멀티 플롯 차트(세로 막대형 + 선형)

---

## 📝 라이선스

본 템플릿은 학습 및 참고 목적의 샘플로 자유롭게 사용 및 커스터마이징이 가능합니다.

---

## 🔖 Keywords / Tags

`ActiveReportsJS` `RDL` `rdlx-json` `Report Designer` `Reporting Tool` `보고서 템플릿` `재고조사 보고서` `Inventory Count Report` `재고 관리` `Inventory Management` `Fixed Page Layout` `Landscape` `조건부 서식` `Conditional Formatting` `Combo Chart` `JavaScript Reporting` `Web Reporting`
