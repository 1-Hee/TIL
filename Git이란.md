# 1. What’s Git?

- Git : 리누스 토르발스가 개발한 분산형 버전 관리 시스템(VCS).
- GitHub : 대표적인 무료 Git 저장소 중 하나 (Service)

## 1.1. 분산형 버전 관리 시스템인 무엇인가?
버전 관리 시스템(VCS)이란, 문서나 설계도, 소스 코드 등의 변경점을 관리해주는 소프트웨어를 말하며, Git은 이런 버전 관리 시스템을 ‘분산형’으로 한다는 것이다. 단어의 뜻 그대로 컴퓨터의 데이터를 여러 컴퓨터에 수평적으로 분산하여 관리하는 VCS인데, 자세한 설명은 아래의 `[1.2. 왜 Git이 필요한가?]` 에 나와 있다.

> Tips
> Git과 GitHub는 시장의 선두주자여서 Git과 GitHub는 일반적으로 같이 짝지어 다뤄지곤 하는데, 엄연히 구분 > 짓는다면 Git과 GitHub 살짝 다른 개념이다.
> - Git : 분산 버전 관리 Programe
> - GitHub : 분산 버전 관리 Service
---------

GitHub는 리누스 토르발즈가 Git을 개발하면서 같이 출범시킨 분산형 버전 관리 시스템 저장소의 하나이고, 이를 대체할 수 있는 경쟁 업체는 지금도 많이 존재한다. 하지만 시장의 선두주자이기도 하고, GitHub의 여러 장점이나 매력 포인트 등 여러 요인들로 인해 GitHub는 시장에서 큰 점유율을 차지하고 있다.

![GitHub Statics](https://kinsta.com/wp-content/uploads/2021/03/collaboration-tool-stack-overflow-survey.jpg)
>2020년 StackOverFlow에서 실시한 설문조사에 따르면 GitHub는 1위를 차지하고 있다.

## 1.3. 왜 Git이 필요한가?
전통적인 데이터 관리 방법은 중앙집중식을 많이 사용했었다. 그러나, 이러한 방법은 만약 중앙의 컴퓨터(ex. Sever)에 문제가 생기면, 하위(Sub) 컴퓨터에도 문제가 생긴다는 약점이 있었다. 그러나, 분산형 버전 관리 시스템 Git은 아래의 그림과 같이 데이터를 수평적으로 관리한다는 특징이 있으며, 이는 어느 한 쪽이 손상되어도 다른 곳에서는 영향을 받지 않으며 이는 곧 Git의 장점이라할 수 있다.

![분산형 VCS](https://img1.daumcdn.net/thumb/R800x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F0206643E51A3776025)

## 1.4. Git WorkFlow

![Git WorkFlow](https://miro.medium.com/max/686/1*diRLm1S5hkVoh5qeArND0Q.png)

Git은 ‘프로그램’이므로 인터넷이 없는 환경에서도 얼마든지 사용할 수 있다.
Git을 사용하기 위해서는 사전에 위의 이미지와 같이 총 3개의 가상 공간이 필요하다.

### 1.4.1. working directory
사용자가 파일을 생성, 편집, 수정, 삭제를 하는 컴퓨터 Local 경로를 의미한다.
일반적으로 사용자가 이용하는 운영체제의 저장소 경로이다.

### 1.4.2. staging area
사용자가 파일을 생성이나 편집 등을 한 내역을 임시로 올리는 곳이다.
working directory에서 git 명령어 중 하나인  git add 를 사용하면, 그 폴더 또는 파일은 staging area에 놓인 상태가 된다.

### 1.4.3. repository
staging area에 놓인 파일을 개발자가 수정을 확정지으면, 변경 이력을 최종적으로 저장하는 공간이다. 
이때 파일이 중복저장되는 것이 아닌 변경된 ‘이력’으로써 관리되므로 데이터 저장을 굉장히 합리적으로 한다고 할 수 있다.

# 2. Git과 명령어
앞선 내용에서는 주로 Git이란 무엇인가에 대한 설명을 적었다.
그렇다면, 이제는 실제 Git 명령어는 어떻게 사용하는지에 대해서 살펴보자.

![GUI vs CLI](data:image/jpeg;base64,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)

GUI란 graphical user interface의 약자로 쉽게 말하자면 window를 떠올리면 된다.
CLI는 일반인은 거의 접하지 않는 interface로 command-line interface의 약자이다.
전자는 일반인도 쉽게 사용할 수 있도록 사용의 편의성이 크고 난이도가 낮은 반면, 후자는 컴퓨터에 대한 기초적인 지식이 있어야 무난하게 사용 가능하며 난이도가 조금 있는 대신 어떤 측면에서는 GUI보다 자유도가 높다고 할 수 있다.

## 2.2. 갑자기 왜 GUI? CUI?
Git은 분산형 버전 관리 시스템인데, aka 프로그램이라고 반복해서 설명했다.
그러나, 기존의 프로그램들은 대부분 많은 사람들이 보편적으로 사용할 수 있도록 GUI를 기반으로 해서 서비스를 제공한다. 그러나 Git은 CLI를 기반으로 사용한다. 그렇기에 다른 일반적인 프로그램과 달리 Git은 사용하기 위해서는 ‘공부’를 조금 더 많이 해야한다는 특징이 있다.


## 2.3. Git의 명령어들
### 2.3.1. git init
git init은 git에 의해 버전관리를 받지 않는 local directory 중에서,
개발자(사용자)가 이제부터 해당 local directory는 git으로 버전관리를 하겠다고,
선언하는 과정이라고 설명할 수 있다.

![S1](./source/0714s1.png)

그래서, git init은 사용할 때 두 가지를 주의하여 사용한다.
 첫째, git을 통해 버전관리 하겠음을 ‘선언’하는 것이므로 최초 1회만 사용해야한다.
 둘째, 가급적 Home directory에는 git init하는 것을 삼가야한다.

두 번째 조건을 주의해야하는 이유는 홈 디렉토리에 git init할 경우,
버전 관리시 온갖 잡다한 것들이 다 관리될 수 있기 때문이다.(비효율적, 비합리적)

### 2.3.2. git add
git add는 working directory에 있는 파일이나 폴더를 git repository에 올리기 전 단계인
staging area에 올려 놓는 명령어이다. 

![S3](.\source\0714s3.png)

`왜 바로 git repository에 올리지 않는 것일까?`

git의 staging area는 단순히 임시로 파일을 올려두는 저장소가 아니다.
staging area는 working directory에서 git repository에 업데이트 하고 싶은 파일이나 폴더를 선별해서 올릴 수 있게 하며, 유사시 잘못 올라간 파일은 취소시키고 git repository에 업데이트 하기 전에 파일이나 폴더에 이상이 없는지 확인할 수 있게 하는 중간 점검을 할 수 있게 하는 공간이다. 그렇기에 staging area는 git에서 중요한 단계이며 꼭 필요한 것이라고 할 수 있다.


### 2.3.3. git commit –m
git은 git commit –m 이라는 명령엉를 통해 변경 이력의 특이사항을 메모할 수 있게 한다.
‘메모’라는 단어에서 선택 옵션인가 하고 생각할 수 있겠지만, 이는 개발자로 협업하는 데에는 ‘필수’ 옵션이다. git을 통해 버전을 관리할 때, 가장 쉽고 간편하고 빠르게 파일의 변경이력을 확인하고 점검하는데에는 git의 commit message를 확인하기 때문이다. 그래서 예컨대 날짜를 메시지로 적는다던가, 업데이트 내역과 무관한 내용을 적는 것은 지양해야한다.
(그래도 굳이 적는다면 git이 막지는 않겠지만 나중에 log로 다 남는다.)

![S4](\source\0714s4.png)
![S5](\source\0714s5.png)

> ▲ git commit –m 양식을 지키지 않았을 때 자동으로 호출되는 Vim 화면.
git은 커밋 메시지를 작성하는 것을 ‘강제’하고 있기 때문에 위와 같은 화면이 등장한다.

이때 탈출하는 방법은 ‘커밋메세지 작성’하는 것이다.
이 화면에서 커밋 메시지 작성하는 방법은
 1. 키보드의 I 키를 눌러서 INSERT 모드로 전환한다. (창 아래에 명기됨)
 2. 메모장에 타자 치듯이 메모를 적는다 (창 상단에 입력됨)
 3. 키보드의 ESC 키를 눌러서 명령어 모드로 전환한다.
 4. 명령어 :wq를 입력하고 엔터를 누르면 원래의 git bash 화면으로 전환된다.

### 2.3.4. git status
현재 디렉토리에서의 git의 현재상태를 알려주는 명령어이다.
다른 명령어 사진을 보면 중간중간 git status가 입력된 것을 볼 수 있는데, git status는 이처럼 git의 각 중간 단계에서 현재 상태를 점검하는 데 쓰이는 명령어이기에 자주 사용되었다.

### 2.4.5. git log
이 명령어는 조금 특별하다(?). 바로 앞 git status와 다르게 git workflow가 repository에 도달하면 쓸 수 있기 때문이다. 이 명령어는 최소 1회 commit이 일어난 경우에만 사용 가능하며 최근에 업데이트된 ‘변경이력’을 보여준다.

![S5](\source\0714s9.png)

또한, 노란색 글씨로 알 수 없는 영어와 숫자가 합쳐진 문자열을 보여주는데, 이것은 해당 repository의 해쉬값이며 고유하다(컴퓨터마다 다르다). 이 ‘해쉬값’은 해당 repository에서 과거의 파일을 보거나 할 때 사용할 key value로써 사용한다. 하지만 주의할 것은 이 행위는 ‘ROLLBACK’시킨다는 의미가 아니다.
