
# 📖 **과제 개요**


## ⛺ **캠프 관리 프로그램**

프로그램 역할 : 내배캠 스프링 수강생들을 관리하는 프로그램

# 📖 **요구사항 정의**

- 캠프에는 필수 과목과 선택 과목이 존재합니다.
    
    
    | 필수 과목 목록 |
    | --- |
    | Java |
    | 객체지향 |
    | Spring |
    | JPA |
    | MySQL |
    
    | 선택 과목 목록 |
    | --- |
    | 디자인 패턴 |
    | Spring Security |
    | Redis |
    | MongoDB |
    
    - 조건
        - 최소 3개 이상의 필수 과목, 2개 이상의 선택 과목을 선택합니다.
        - 캠프 기간동안 선택한 과목별로 총 10회의 시험을 봅니다.
        - 캠프 매니저는 수강생을 등록 및 관리할 수 있습니다.
        - 캠프 매니저는 수강생들의 과목과 시험 점수를 등록 및 관리할 수 있습니다.
        - 점수 데이터 타입 : 정수형
        - 점수에 따라 등급이 매겨집니다.
            - 과목: Java
                
                
                | 1회차 | 2회차 | 3회차 | … |
                | --- | --- | --- | --- |
                | D | D | B | … |
        - 등급 산정 기준
            - 필수 과목
                
                
                | A | B | C | D | F | N |
                | --- | --- | --- | --- | --- | --- |
                | 95 ~ 100 | 90 ~ 94 | 80 ~ 89 | 70 ~ 79 | 60 ~ 69 | 60점 미만 |
            - 선택 과목
                
                
                | A | B | C | D | F | N |
                | --- | --- | --- | --- | --- | --- |
                | 90 ~ 100 | 80 ~ 89 | 70 ~ 79 | 60 ~ 69 | 50 ~ 59 | 50점 미만 |
    - 모델 정보 예시
        
        
        | 수강생 |
        | --- |
        | 고유 번호 |
        | 이름 |
        | 과목 목록 |
        
        | 점수 |
        | --- |
        | 과목 고유 번호 |
        | 수강생 고유 번호 |
        | 회차 |
        | 점수 |
        | 등급 (A, B, C, D, E, F, N) |
        
        | 과목 |
        | --- |
        | 고유 번호 |
        | 과목명 |
        | 과목타입 (필수, 선택) |


# 📖 **기능 명세서**


- **필수 요구 사항**
    
    ⚙ **수강생 관리**
    
    - 주의‼️
        - 수강생의 고유번호는 중복될 수 없습니다.
    1. 수강생 정보를 등록할 수 있습니다.
        
        
        | 등록 필수 정보 |
        | --- |
        | 고유 번호 |
        | 이름 |
        | 과목 목록 |
    2. 수강생 목록을 조회할 수 있습니다. 조회 형식은 자유입니다.
        
        
        | 조회 필수 정보 |
        | --- |
        | 고유 번호 |
        | 이름 |
    
    ⚙ **점수 관리**
    
    - 주의‼️
        - 등록하려는 과목의 회차 점수가 이미 등록되어 있다면 등록할 수 없습니다. 과목의 회차 점수가 중복되어 등록될 수 없습니다.
        - 회차에 10 초과 및 1 미만의 수가 저장될 수 없습니다. (회차 범위: 1 ~ 10)
        - 점수에 100 초과 및 음수가 저장될 수 없습니다. (점수 범위: 0 ~ 100)
    1. 수강생의 과목별 시험 회차 및 점수를 등록할 수 있습니다.
        - 점수를 등록하면 자동으로 등급이 추가 저장됩니다.
    2. 수강생의 과목별 회차 점수를 수정할 수 있습니다.
    3. 수강생의 특정 과목 회차별 등급을 조회할 수 있습니다.
        - 조회 형식은 자유입니다.
            
            
            | 조회 필수 정보 |
            | --- |
            | 회차 |
            | 등급 |

    

---

- **추가 요구 사항**
    
    ⚙ **수강생 관리**
    
    1. 수강생 상태를 관리할 수 있습니다.
        
        
        | 상태 종류 |
        | --- |
        | Green |
        | Red |
        | Yellow |
    2. 수강생 정보를 조회할 수 있습니다. 조회 형식은 자유입니다.
        
        
        | 조회 필수 정보 |
        | --- |
        | 고유 번호 |
        | 이름 |
        | 상태 |
        | 선택한 과목명 |
    3. 수강생 정보를 수정할 수 있습니다.
        - 이름 또는 상태를 입력받아 수정하시면 됩니다.
        
        | 수정 가능한 정보 |
        | --- |
        | 이름 |
        | 상태 |
    4. 상태별 수강생 목록을 조회할 수 있습니다. 조회 형식은 자유입니다.
        
        
        | 조회 필수 정보 |
        | --- |
        | 고유 번호 |
        | 이름 |
    5. 수강생을 삭제할 수 있습니다.
        - 해당 수강생의 점수 기록도 함께 삭제됩니다.
  
    ⚙ **점수 관리**
    
    1. 수강생의 과목별 평균 등급을 조회할 수 있습니다. 조회 형식은 자유입니다.
        
        
        | 조회 필수 정보 |
        | --- |
        | 과목명 |
        | 평균 등급 |
    2. 특정 상태 수강생들의 필수 과목 평균 등급을 조회합니다. 조회 형식은 자유입니다.
        
        
        | 조회 필수 정보 |
        | --- |
        | 수강생 이름 |
        | 필수 과목 평균 등급 |


# 📖 **선택 사항**


- 객체지향 및 클래스 설계가 아직 익숙하지 않은 팀은 준비된 **Template**을 기반으로 시작해도 괜찮습니다.
    - 해당 **Template**은 필수 요구 사항 구현을 쉽게 시작 해볼 수 있도록 설계된 소스코드 틀입니다.
    - Template 프로젝트의 클래스에 필요한  필드와 메서드가 전부 구현 되어있지는 않습니다.
        - 필요한 필드와 메서드는 직접 구현 해주셔야 합니다.
    - **Template 프로젝트**
        
        [camp-management-app.zip](https://prod-files-secure.s3.us-west-2.amazonaws.com/83c75a39-3aba-4ba4-a792-7aefe4b07895/11e5366a-3ecd-40b0-ad31-afd6fb00583c/camp-management-app.zip)
        
- 객체지향 및 클래스 설계가 익숙하신 팀은 요구사항 정의와 기능 명세서를 기반으로 직접 설계하여 구현해보시는 것을 추천드립니다.

# 📖 **우리가 만든 과제가 잘 돌아가는 지 확인하려면?**


### **⚙️ 테스트(이런 식으로 테스트 해보세요!)**

### 시나리오 테스트

시나리오 테스트는 작성한 프로젝트 및 코드가 정상적으로 동작 하는지 테스트하는 방식중에 하나 입니다.

프로그램을 사용하는 사용자의 행동을 예측하여 가상의 시나리오를 설정하고 그 시나리오 대로 프로그램을 실행하면 됩니다.

### 엣지 케이스 테스트

엣지 케이스 테스트는 정상적인 시나리오가 아닌 예상외로 흘러갔을 때 어떻게 동작 하는지 테스트 하는 방식중에 하나 입니다.
이를 통해서 다양한 예외처리 및 시스템의 안정성을 확보 할 수 있습니다.

- **테스트 예시**
    - 수강생 관리 (엣지 케이스 적용한 케이스)
        - 예제 1
            - 1. 프로그램 메인 페이지에서 수강생 관리 항목으로 들어간 다음, 수강생 관리를 선택합니다. 먼저, 수강생 이름을 입력하면 필수 과목 3개 이상, 선택 과목 2개 이상을 선택할 수 있습니다.
            - 테스트 케이스1 : 2개의 필수 과목, 선택 과목 2개를 선택합니다.
                - 예상 결과 : 최소 3개 이상의 필수 과목, 선택 과목 2개 이상이 선택되지 않았기 때문에, 해당 내용이 안내되고 등록되지 않아야 합니다.
            - 테스트 케이스2 : 3개 이상의 필수 과목, 선택 과목 2개 이상을 선택합니다.
                - 예상 결과 : 요구 조건에 부합하기 때문에 수강생 등록에 성공!
        - 예제 2
            - 2. 프로그램 메인 페이지에서 수강생 관리 항목으로 들어간 다음, 수강생 목록 조회를 할 수 있습니다.  수강생 목록 조회 시, 등록되어 있는 수강생이 전부 나와야 합니다.
                - 예상결과 : 1에서 2개의 필수 과목, 선택 과목 2개 선택했던 내용 및 수강생이 저장되지 않은 것이 맞는지 확인합니다. 해당 조건을 제대로 수행한 수강생이 목록에 있는지 확인합니다.
                
    - 점수 관리 예제 (시나리오 테스트를 적용한 케이스)
        
        **여기서 보여주는 예시대로 출력할 필요는 없습니다.  참고를 위한 예시입니다.**
        
        - 예제 1 : 점수 등록하고 조회하기
          
            
            시나리오 . 뒤늦게 내배캠에 합류한 수강생의 점수를 입력합니다. 1차 (미니 프로젝트 주차)는 참여하지 않았으니 0점으로 기록하고 2차(자바)는 참여하여 90점의 점수를 확보하였습니다.
            내배캠의 관리자는 위의 수강생을 해당 프로그램을 사용하여 점수를 입력하고 잘 입력 되었는지 확인합니다. 
            
            1. 점수 관리 기능에 들어간다. 
            
            
            1. 수강생 점수 등록
                
                
            2. 수강생 점수 조회
            
        - 예제 2 : 점수 수정하기
            
            시나리오 : 시험 성적을 90 점을 입력해야 했는데 9점을 입력하여 점수 수정이 필요하다.
            
            점수를 수정하고 점수가 잘 수정 되었는지 확인한다.
            
            1. 점수 수정 기능에 들어간다.
                
                
            2. 점수를 수정한다.
                
                
            3. 수정된 점수를 확인힌다.
                
                

# 📖 **발표에 어떤 내용이 들어가야 하나요?**


## 처음으로 자바로 진행하는 팀 과제

이번 팀 과제는 앞으로 있을 스프링 팀과제를 진행하기 전에 진행되는 리허설 입니다.

본격적인 스프링 주차 협업 프로젝트가 진행되기 전에 아래의 내용들을 경험하고 가져 갈 수 있습니다.

- 혼자 진행했던 개인 프로젝트 수준의 개발을 **협업하여 팀이랑 같이 진행하기**
- 원활한 협업을 위한 역할 분담
- 동시에 진행되는 프로젝트 관리 경험 (conflict 지옥 경험)

## 어떤 내용으로 발표하면 좋을까?

**‼️모든 내용이 들어갈 필요는 없습니다‼️**

- 역할 분담 선정의 이유 역할 분담을 나눈 기준 등
    - ex) 우리는 점수  관리 기능, 유저 등록 관리 기능을 기준으로 팀을 나눠서 진행했습니다
    - ex) 우리는 필수 요구사항 번호대로 1개씩 담당해서 역할을 나눴습니다
- 트러블 슈팅
    - ex) 동시에 진행한 프로젝트를 하나의 파일로 머지하는 과정에서 수많은 충돌이 났었다. 
    이런 충돌을 이런 방식을 해결했다.
    - ex) 구체적인 내용물 없이 개발을 시작하다보니 서로 설정 및 내용이 달라서 합치는 과정에서 문제가 많을 것이라고 생각했다. 그래서 우리는 먼저 공동으로 사용되는 모델들을 먼저 같이 개발하고 그 이후에 담당한 역할 별로 개발을 진행하였다.
- 코드적으로 자랑하고 싶은 것 1~2 가지 (간략한 코드 설명 포함)
    - ex) 우리팀은 예외 처리(엣지 케이스)를 이렇게 까지 꼼꼼하게 처리했다.
    - ex) 우리팀은 인터페이스, 상속 등을 활발하게 사용하였다.
    - ex) 우리팀은 제네릭을 사용하여 구현했다
    

# 📖 **과제 제출**


- 제출 기한 : 8월 8일 (목) 09시까지
- 발표회 : 8월 8일 (목) 14:00
    - 자세한 일정은 추후 공지하겠습니다.
    
    ☝🏻 주의사항!
    
    이번에는 S.A 제출을 하지 않습니다.
    
    API 명세와 와이어 프레임 구성 대신, 이번 팀 과제를 위해 필요한 Ground Rules을 정해봐요!
   
    

# 💡 **협업 가이드**


> 첫 팀 과제! 

“협업을 위한 Github 가이드라인”을 확인하시고 
차근차근 GitHub Repository에 commit push merge까지 도전해봅시다!
> 
> 
> [협업을 위한 Github 가이드라인](https://www.notion.so/Github-add94136c00d4dc28ffc3c219a19a6ff?pvs=21)
> 

# 💡 **혹시, 개인 과제가 조금 버거우셨나요?**


1. 자바가 또는 코딩이 처음이라면, 당연히 낯설게 느껴질 수 밖에 없죠.
2. 또한 다른 언어에 비해 상대적으로 한 단계 정도 어려운 언어입니다. 하지만 못 배울 정도로 어려운 언어는 절대 아닙니다.
3. 지금 제일 중요한 것은 ‘강의를 듣는 것’ 입니다.
    1. 내가 지금 어느 위치에 있는 지 정확하게 파악 하는 것이 중요합니다. 
    2. 주특기 기초 주차에서 본격적으로 스프링을 공부하게 됩니다. 이 전에 자바에 대한 어느 정도의 이해를 가지고 있어야 합니다.
4. 위 데이터를 바탕으로 특강 또는 보충 강의가 준비될 예정입니다.
