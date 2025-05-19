# C011130


# 공유 자전거 대여 시스템 설계 문서

## 1. Functional Requirement List (기능 요구사항)

1. 사용자는 시스템 이용을 위해 회원 가입을 할 수 있다.  
   - 입력 정보: ID, 비밀번호, 전화번호

2. 관리자는 주어진 ID(admin)와 비밀번호(admin)로 로그인할 수 있다.

3. 사용자(회원/관리자)는 ID와 비밀번호를 통해 로그인할 수 있으며, 로그아웃 기능을 이용해 시스템에서 로그아웃할 수 있다.

4. 관리자는 자전거 ID 및 자전거 제품명을 이용해 자전거를 등록할 수 있다.

5. 회원은 등록된 자전거를 선택하여 대여할 수 있다.

6. 회원은 자신이 대여 중인 자전거 목록을 조회할 수 있다.  
   - 출력 정보: 자전거 ID, 자전거 제품명

---


## 3. Use Case Descriptions

### Use Case 1: 회원 가입
- **Actor:** 사용자  
- **Precondition:** 없음  
- **Flow:**
  1. 사용자는 ID, 비밀번호, 전화번호를 입력한다.
  2. 시스템은 중복 ID 여부를 확인한다.
  3. 유효한 경우 회원 정보를 저장하고 가입을 완료한다.

### Use Case 2: 로그인
- **Actor:** 회원/관리자  
- **Flow:**
  1. 사용자 ID와 비밀번호 입력
  2. 시스템은 일치 여부를 확인하여 접속 허용

### Use Case 3: 로그아웃
- **Actor:** 회원/관리자  
- **Flow:**
  1. 사용자 요청 시 시스템에서 세션 종료

### Use Case 4: 자전거 등록
- **Actor:** 관리자  
- **Flow:**
  1. 관리자 로그인
  2. 자전거 ID, 제품명 입력
  3. 시스템이 등록된 자전거 목록에 추가

### Use Case 5: 자전거 대여
- **Actor:** 회원  
- **Flow:**
  1. 로그인 후 회원이 자전거 선택
  2. 시스템이 대여 가능한 상태인지 확인 후 대여 처리

### Use Case 6: 대여 정보 조회
- **Actor:** 회원  
- **Flow:**
  1. 로그인한 회원이 대여정보 조회 요청
  2. 시스템은 회원이 현재 대여 중인 자전거 리스트를 보여줌

---

## 4. Communication Diagram (텍스트 설명)

**시나리오:** 회원이 로그인한 후 자전거를 대여하는 과정  

**객체:** `User`, `LoginController`, `BikeController`, `BikeDB`

**메시지 흐름:**
1. `User -> LoginController`: 로그인 정보 입력 (ID, PW)
2. `LoginController -> User`: 인증 결과 반환
3. `User -> BikeController`: 자전거 대여 요청 (bikeID)
4. `BikeController -> BikeDB`: 대여 가능 여부 확인
5. `BikeDB -> BikeController`: 사용 가능
6. `BikeController -> User`: 대여 완료 응답

---
