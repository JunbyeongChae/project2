# 냉장고 및 식재료 관리 웹페이지 개발 계획서

## 1. 프로젝트 개요

냉장고와 그 외의 식재료를 체계적으로 관리하는 웹페이지를 개발하고자 합니다. 사용자는 회원가입을 통해 자신의 냉장고에 있는 재료를 쉽게 입력하고 관리할 수 있으며, AI를 활용한 레시피 추천 기능을 통해 유용한 요리 정보를 제공합니다. 본 웹페이지는 식재료의 유통기한 관리 및 재고 알림 기능 등을 통해 사용자 편의성을 극대화하는 것을 목표로 합니다.

## 2. 주요 기능

### 2.1 회원가입 / 로그인

- **기능 설명**: 사용자는 계정을 생성하고 로그인할 수 있습니다. 이 기능을 통해 각 사용자의 재료 정보와 레시피 추천 결과 등을 개별적으로 관리할 수 있습니다.
- **기술 스택**: JWT를 활용한 인증, 이메일 인증 절차 포함.

### 2.2 재료 입력

- **입력 항목**: 재료명, 유통기한, 보관 장소(냉장/냉동/실온), 보관 방법 등.
- **기능 설명**: 사용자가 현재 보유하고 있는 식재료를 등록할 수 있습니다. 재료 입력 후 재료에 대한 정보를 데이터베이스에 저장합니다.

### 2.3 AI 레시피 추천

- **기능 설명**: 등록된 재료들을 바탕으로 OpenAI의 GPT 모델을 활용하여 해당 재료로 만들 수 있는 다양한 요리를 추천합니다. 사용자 맞춤형 요리를 제안하여 식재료 활용도를 높이는 것이 목표입니다.
- **기술 스택**: OpenAI API, Node.js (Express 등).

### 2.4 재료 관리

- **유통기한 알림**: 재료 유통기한 임박 시 또는 초과 시 사용자에게 알림을 제공합니다.
- **기술 스택**: 백엔드 서버에서 주기적으로 유통기한을 검사하고 알림 시스템을 통해 사용자에게 알림 (예: 이메일, 푸시 알림).

### 2.5 재고 관리 및 쇼핑 리스트 생성

- **재고 관리**: 현재 재고를 관리하고, 특정 재료가 소진될 경우 재구매가 필요함을 사용자에게 알림.
- **쇼핑 리스트 등록**: 부족한 재료는 쇼핑 리스트에 추가할 수 있으며, 사용자는 쇼핑 리스트를 별도로 관리할 수 있습니다.
- **기술 스택**: 데이터베이스와 연동된 재고 및 쇼핑 리스트 관리 모듈.

## 3. 추가 고려 기능

- **레시피 저장 및 공유**: 사용자가 마음에 드는 레시피를 저장하고 다른 사용자와 공유할 수 있는 기능.
- **가족 계정 기능**: 가족 구성원과 계정을 공유하여 서로의 재료 목록을 공동으로 관리.
- **음성 인식 기능**: 음성으로 재료를 입력하거나, 레시피를 요청할 수 있는 기능을 추가하여 사용자 편의성 향상.
- **QR 코드 연동**: 재료 구매 시 QR 코드를 스캔하여 간편하게 재료 정보를 등록할 수 있는 기능.
- **식재료별 보관 방법 안내**: AI를 활용해 각 재료의 최적 보관 방법을 안내해주는 기능.

## 4. 개발 환경 및 기술 스택

- **프론트엔드**: HTML, CSS, JavaScript (사용자 인터페이스 개발).
- **백엔드**: Node.js (Express 등) (API 및 서버 구축).
- **데이터베이스**: MySQL (재료 및 사용자 정보 관리).
- **AI 연동**: OpenAI API (레시피 추천 기능).
- **인증 및 보안**: JWT 기반 인증, HTTPS 보안 통신.

## 5. 개발 일정

1. **1주차**: 요구사항 분석 및 설계.
2. **2주차**: 회원가입/로그인 및 재료 입력 기능 구현.
3. **3주차**: AI 레시피 추천 기능 개발 및 테스트.
4. **4주차**: 재료 및 재고 관리 기능 구현.
5. **5주차**: 추가 기능 구현 및 통합 테스트.
6. **6주차**: 사용자 피드백 수집 및 최종 수정.

## 6. 예상 문제 및 해결 방안

- **API 호출 비용 관리**: OpenAI API 사용 시 비용이 발생하므로, 호출 빈도를 최적화하고 캐싱 등을 통해 비용을 절감.
- **유통기한 알림의 정확성**: 사용자가 정확히 입력하지 않을 가능성이 있으므로, 재료 입력 시 유효성 검사를 강화하여 정확성을 높임.

## 7. 화면 구성

### 7.1 홈 화면

- **구성 요소**: 로그인 상태에 따라 다르게 표시되며, 로그인하지 않은 사용자는 회원가입 및 로그인 버튼을 볼 수 있습니다. 로그인한 사용자는 보유 재료의 간략한 현황과 임박한 유통기한 알림을 확인할 수 있습니다.
- **주요 기능**: 회원가입, 로그인, 유통기한 임박 재료 알림.

### 7.2 회원가입 / 로그인 화면

- **구성 요소**: 이메일과 비밀번호 입력 창, 회원가입 버튼 및 로그인 버튼.
- **주요 기능**: 사용자 계정 생성 및 로그인 처리.

### 7.3 재료 입력 화면

- **구성 요소**: 재료명, 유통기한, 보관 장소(냉장/냉동/실온), 보관 방법을 입력할 수 있는 폼.
- **주요 기능**: 재료 정보 입력 및 데이터베이스 저장.

### 7.4 재료 목록 화면

- **구성 요소**: 사용자가 등록한 모든 재료의 목록이 테이블 형식으로 표시됩니다. 각 재료는 이름, 유통기한, 보관 장소 등의 정보가 함께 나타납니다.
- **주요 기능**: 재료 수정 및 삭제, 유통기한에 따른 정렬 및 필터링.

### 7.5 레시피 추천 화면

- **구성 요소**: 사용자가 보유한 재료 목록을 기반으로 AI가 추천한 레시피 목록이 카드 형식으로 표시됩니다.
- **주요 기능**: 레시피 상세 보기, 재료 추가 정보 제공.

### 7.6 재고 관리 화면

- **구성 요소**: 현재 보유 중인 재료의 재고 상태를 한눈에 볼 수 있으며, 부족한 재료는 강조 표시됩니다.
- **주요 기능**: 재고 추가 및 소진 표시, 쇼핑 리스트에 추가.

### 7.7 쇼핑 리스트 화면

- **구성 요소**: 사용자가 재구매가 필요하다고 표시한 재료 목록.
- **주요 기능**: 재료 구매 완료 시 체크하여 쇼핑 리스트에서 제거.

## 8. 결론

이 웹페이지는 식재료 관리의 번거로움을 줄이고, AI를 활용하여 더욱 효율적인 가정 내 식재료 활용을 돕고자 합니다. 이 프로젝트를 통해 사용자들에게 더욱 유용하고 스마트한 주방 환경을 제공할 수 있을 것으로 기대됩니다.