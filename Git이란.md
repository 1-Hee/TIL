

# 1. What’s Git?

- Git : 리누스 토르발스가 개발한 분산형 버전 관리 시스템(VCS).
- GitHub : 대표적인 무료 Git 저장소 중 하나 (Service)



## 1.1. 분산형 버전 관리 시스템인 무엇인가?
 버전 관리 시스템(VCS)이란, 문서나 설계도, 소스 코드 등의 변경점을 관리해주는 소프트웨어를 말하며, Git은 이런 버전 관리 시스템을 ‘분산형’으로 한다는 것이다. 단어의 뜻 그대로 컴퓨터의 데이터를 여러 컴퓨터에 수평적으로 분산하여 관리하는 VCS인데, 자세한 설명은 아래의 `[1.2. 왜 Git이 필요한가?]` 에 나와 있다.



> 💡 Tips
> Git과 GitHub는 시장의 선두주자여서 Git과 GitHub는 일반적으로 같이 짝지어 다뤄지곤 하는데, 엄연히 구분 짓는다면 Git과 GitHub 살짝 다른 개념이다.
>
> - Git : 분산 버전 관리 Programme
> - GitHub : 분산 버전 관리 Service
---------



 GitHub는 리누스 토르발즈가 Git을 개발하면서 같이 출범시킨 분산형 버전 관리 시스템 저장소의 하나이고, 이를 대체할 수 있는 경쟁 업체는 지금도 많이 존재한다. 하지만 시장의 선두주자이기도 하고, GitHub의 여러 장점이나 매력 포인트 등 여러 요인들로 인해 GitHub는 시장에서 큰 점유율을 차지하고 있다.



![GitHub Statics](https://kinsta.com/wp-content/uploads/2021/03/collaboration-tool-stack-overflow-survey.jpg)
>2020년 StackOverFlow에서 실시한 설문조사에 따르면 GitHub는 1위를 차지하고 있다.

## 1.3. 왜 Git이 필요한가?
 전통적인 데이터 관리 방법은 중앙집중식을 많이 사용했었다. 그러나, 이러한 방법은 만약 중앙의 컴퓨터(ex. Sever)에 문제가 생기면, 하위(Sub) 컴퓨터에도 문제가 생긴다는 약점이 있었다. 그러나, 분산형 버전 관리 시스템 Git은 아래의 그림과 같이 데이터를 수평적으로 관리한다는 특징이 있으며, 이는 어느 한 쪽이 손상되어도 다른 곳에서는 영향을 받지 않으며 이는 곧 Git의 장점이라할 수 있다.



![분산형 VCS](https://img1.daumcdn.net/thumb/R800x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F0206643E51A3776025)

> 좌측 이미지는 전통적인 중앙집중식, 우측은 Git의 분산형 버전관리 방법이다.



## 1.4. Git WorkFlow

![Git WorkFlow](https://miro.medium.com/max/686/1*diRLm1S5hkVoh5qeArND0Q.png)



Git은 ‘프로그램’이므로 인터넷이 없는 환경에서도 얼마든지 사용할 수 있다.
Git을 사용하기 위해서는 사전에 위의 이미지와 같이 **총 3개의 공간** 이 필요하다.

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



![GUI vs CLI](https://cli.pub/medias/sites/54/2021/02/s-guicommand-line-interface-graphical-user-interface-in-urdu-and-hindi-9gseCS7ljuk.jpg)



 GUI란 **Graphical User Interface** 의 약자로 쉽게 설명하자면 window를 떠올리면 된다. CLI는 일반인은 거의 접하지 않는 interface로 **command-line interface** 의 약자이다. 전자는 일반인도 쉽게 사용할 수 있도록 사용의 편의성이 크고 난이도가 낮은 반면, 후자는 컴퓨터에 대한 기초적인 지식이 있어야 무난하게 사용 가능하며 난이도가 조금 있는 대신 어떤 측면에서는 GUI보다 자유도가 높다고 할 수 있다.



## 2.1. GUI?, CLI?
Git은 분산형 버전 관리 시스템인데, aka 프로그램이라고 반복해서 설명했다.
그러나, 기존의 프로그램들은 대부분 많은 사람들이 보편적으로 사용할 수 있도록 GUI를 기반으로 해서 서비스를 제공한다. 그러나 Git은 CLI를 기반으로 사용한다. 그렇기에 다른 일반적인 프로그램과 달리 Git은 사용하기 위해서는 ‘공부’를 조금 더 많이 해야한다는 특징이 있다. `CLI`는 종류가 여러가지 존재하고, 그 중에서 `LINUX 명령어` 에 대해서는 간략하게 명령어만 별도의 마크다운`.md`으로 정리해 두었다.








## 2.2. Git의 명령어들
### 2.2.1. git init
 git init은 git에 의해 버전관리를 받지 않는` local directory ` 중에서 개발자(사용자)가 이제부터 해당 local directory는 git으로 버전관리를 하겠다고  선언하는 과정이라고 설명할 수 있다.

![0714S1](https://github.com/1-Hee/TIL/blob/master/source/0714s1.PNG?raw=true)

 그래서, git init은 사용할 때 두 가지를 주의하여 사용한다. 첫째, git을 통해 버전관리 하겠음을 ‘선언’하는 것이므로 최초 1회만 사용해야한다. 둘째, 가급적 `Home directory`에는 `git init`하는 것을 삼가야한다. 두 번째 조건을 주의해야하는 이유는 홈 디렉토리에 `git init` 할 경우, 버전 관리시 온갖 잡다한 것들이 다 관리될 수 있기 때문이다 (비효율적, 비합리적).



### 2.2.2. git add
 `git add`는 working directory에 있는 파일이나 폴더를 git repository에 올리기 전 단계인 staging area에 올려 놓는 명령어이다. 

![0714S3](https://github.com/1-Hee/TIL/blob/master/source/0714s3.PNG?raw=true)

>  `🤔 git은 왜 바로 git repository에 올리지 않는 것일까?`



 git의 `staging area`는 단순히 임시로 파일을 올려두는 저장소가 아니다. `staging area`는 `working directory`에서 `git repository` 에 업데이트 하고 싶은 파일이나 폴더를 선별해서 올릴 수 있게 하며, 유사시 잘못 올라간 파일은 취소시키고 `git repository` 에 업데이트 하기 전에 파일이나 폴더에 이상이 없는지 확인할 수 있게 하는 중간 점검을 할 수 있게 하는 공간이다. 그렇기에 `staging area`는 git에서 중요한 단계이며 꼭 필요한 것이라고 할 수 있다.


### 2.2.3. git commit –m
git은 `git commit –m` 이라는 명령어를 통해 변경 이력의 특이사항을 메모할 수 있게 한다. `메모` 라는 단어에서 선택 옵션인가 하고 생각할 수 있겠지만, 이는 개발자로 협업하는 데에는 `필수` 옵션이다. git을 통해 버전을 관리할 때, 가장 쉽고 간편하고 빠르게 파일의 변경이력을 확인하고 점검하는데에는 git의 **commit message**를 확인하기 때문이다. 그래서 예컨대 날짜를 메시지로 적는다던가, 업데이트 내역과 무관한 내용을 적는 것은 지양해야한다. (그래도 굳이 적는다면 git이 막지는 않겠지만 나중에 log로 다 남는다.)



![0714S4](https://github.com/1-Hee/TIL/blob/master/source/0714s4.PNG?raw=true)

![0714S5](https://github.com/1-Hee/TIL/blob/master/source/0714s5.PNG?raw=true)

> ▲ `git commit –m` 양식을 지키지 않았을 때 자동으로 호출되는 Vim 화면.
git은 커밋 메시지를 작성하는 것을 ‘강제’하고 있기 때문에 위와 같은 화면이 등장한다.



이때 탈출하는 방법은 ‘커밋메세지 작성’하는 것이다. 이 화면에서 커밋 메시지 작성하는 방법은

  1. 키보드의 `I` 키를 눌러서 **INSERT 모드** 로 전환한다. (창 아래에 명기됨)
  2. 메모장에 타자 치듯이 메모를 적는다 (창 상단에 입력됨)
  3. 키보드의 `ESC` 키를 눌러서 **명령어 모드** 로 전환한다.
  4. 명령어 `:wq`를 입력하고 엔터를 누르면 원래의 **git bash** 화면으로 전환된다.



### 2.2.4. git status
 현재 디렉토리에서의 git의 현재상태를 알려주는 명령어이다. 다른 명령어 사진을 보면 중간중간 `git status`가 입력된 것을 볼 수 있는데, git status는 이처럼 git의 각 중간 단계에서 현재 상태를 점검하는 데 쓰이는 명령어이기에 자주 사용되었다.

### 2.2.5. git log
이 명령어는 조금 특별하다(?). 바로 앞 `git status`와 다르게 **git workflow**가 **repository**에 도달하면 쓸 수 있기 때문이다. 이 명령어는 최소 1회 **commit이 일어난 경우** 에만 사용 가능하며 최근에 업데이트된 ‘변경이력’을 보여준다.

![0714S5](https://github.com/1-Hee/TIL/blob/master/source/0714s9.PNG?raw=true)

 또한, 노란색 글씨로 알 수 없는 영어와 숫자가 합쳐진 문자열을 보여주는데, 이것은 해당 `repository`의 `해쉬값`이며 고유하다 (컴퓨터마다 다르다). 이 ‘해쉬값’은 해당 repository에서 과거의 파일을 보거나 할 때 사용할 **key value** 로써 사용한다. 하지만 주의할 것은 이 행위는 ‘ROLLBACK’시킨다는 의미가 아니다.

### 2.2.6. git log --online

 `2.3.5. git log`를 참조하면, `git log` 라는 명령어는 다소(?) 상세한 정보들을 표시해준다. 그런데, Git은 버전관리 프로그램이기 때문에 당연히 해당 폴더에서 작업을 하면 할 수록 시간의 흐름과 함께 점점 `commit` 내역들이 쌓여갈 것이다. 만약 이 상황에 대해 어떤 해결책이 없다면 개발자들은 개발을 시작한지 오래된 폴더에서 `git pull`을 하고 `git log` 를 찍으면 고작 한 줄짜리 명령어가 자칫하면 수십, 수백 줄의 결과 코드를 반환할 수 있으니 항상 걱정이 가득해야 할지도 모르겠다. 하지만 다행히 똑똑한 개발자들은 그렇게 해두지 않았다. git log의 코드가 누적되어 양이 많아지면 일정 수준 이하로 자동으로 편집을 해버리며, 그 화면은 다음과 같다.



![0715s1](https://github.com/1-Hee/TIL/blob/master/source/0715s1.PNG?raw=true)

![0715s2](https://github.com/1-Hee/TIL/blob/master/source/0715s2.PNG?raw=true)



 코드가 길어지면 위의 이미지와 같이 log 내역이 전부다 나타나지 않는다. 저 화면에서는 콘솔창이 마치 먹통(?)이된 것 같은 상황이 발생하는데, 이때에는 어떤 입력이나 스크롤도 맘대로 되지 않아서 패닉에 빠질 수 있다. 이때에도 **Vim 에디터** 에서 했던 것처럼 `wq` 를 입력하면 빠져나올 수 있다.



### 2.2.7. git checkout 해쉬값

 그동안 `git add` , `git commit - m` , `git push origin master` 등을 잘 사용했고, `git log`를 입력해서 `commit` 내역을 확인하는 것까지 순조로웠다면 아래와 같은 의문이 들 수 있을 것 같다.



>  git이 버전관리를 한다는데, 도대체 어떻게 버전관리로 한다는 거지? 어떻게 버전별로 접근을 하는 걸까?



위의 질문에 대한 해답은 바로 여기서 얻을 수 있다. 바로 git의 **해쉬값** 을 통해서 지난 버전들에 접근하고 관리할 수 있다. local에서 `git commit -m` 을 통해 변경 이력을 저장했다면, 그 이력은 고유한 값인 **해쉬값**을 가진다. 이 해쉬 값은 컴퓨터마다 전혀 다르고 '고유'하기 때문에 겹칠 수가 없다. 그래서 이 값을 기준으로 해당 폴더나 파일의 버전 관리를 할 수 있게 된다.



![0715S7](https://github.com/1-Hee/TIL/blob/master/source/0715s7.PNG?raw=true)

>  git checkout 해쉬값을 입력했을 때 볼 수 있는 git bash 창이다. 컴퓨터 디렉토리 우측 괄호의 값이 변했다.



 `git checkout 해쉬값` 은 위의 사진과 같이 과거의 파일을 접근할 수 있게 해주며, 현재 파일에 스크린 샷으로 담지 않았지만, 특정 해쉬값을 입력하면 그 해쉬값에 해당하는 변경이력 까지 파일을 복원한다. (미래의 이력은 안보이게 해줌) 이때 유의할 것은 이 명령어가 그동안의 `commit` 이력을 `ROLLBACK`하는 것이 아니라는 점이다.



### 2.2.8.  git rm --cached 

 git에 업로드를 하다 보면, 파일을 잘못 올려버린 경우가 생길 수 있다. `git add`를 사용하면 파일은 곧바로 `staging area`에 올라가는 것이지 곧바로 `repository`에 올라가는 것이 아니기 때문에 잘못 올라간 파일을 취소 시킬 수 있다. 여기서 다시한번 `staing area`의 진가가 발휘하는 대목인 것 같다.



```
DESKTOP MINGW64 /d/.test (master)
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   b.txt

```

` git add`를 입력하고 bash 창을 확인하면 위와 같은 결과 코드를 볼 수 있다. 이때 git은 친절하게 파일을 올렸다는 '정보'와 잘못 올린 경우를 대비하여 취소하는 명령어를 같이 안내해주는데, 잘못 올린 파일을 취소하는 명령어가 바로 `git rm --cached ` 이다. 이 명령어 뒤에 삭제하고 싶은 파일명을 입력하면 add된 것이 취소된다.



### 2.2.9. git commit --amend

  git에서 commit을 한 뒤에 갑자기 내가 작성한 commit message가 마음에 안들 수 있다. 그렇다면 이것을 수정하려면 새롭게 수정해서 또 commit을 해야할까? 정답은 아니다. git에서는 이러한 상황에 대비하여 commit이 된 이후라도 메세지를 수정할 수 있는 명령어를 제공하며 그것이 바로 `git commit --amend` 이다. 단, 이때 주의할 것은 이 명령어를 쓰면 무조건 Vim 편집기가 나타나게 되는데, 사용법은 위에 설명한 만큼 당황하지 않고 메세지를 편집 후 빠져나와주면 생각보다 쉽게 메세지를 편집할 수 있다.

![0714S5](https://github.com/1-Hee/TIL/blob/master/source/0714s5.PNG?raw=true)

> `2.3.3. git commit –m` 챕터에서 다룬 Vim 에디터  사진이다. `git commit --amend`를 입력하면 직전 커밋 내역에 대한 Vim 에디터가 활성화 된다.



### 2.2.10. git remote -v

>  GitHub와 Local의 Bridge를 확인하는 방법

간단히 설명하겠다. 이 명령어를 사용하면 현재 폴더가 어느 GitHub와 Link되었는지 확인 가능하다.

```
DESKTOP MINGW64 /d/.test (master)
$ git remote -v
origin  https://github.com/사용자명/레포지토리.git (fetch)
origin  https://github.com/사용자명/레포지토리.git (push)
```



### 2.2.11. git clone

추가 편집...



### 2.2.12. git pull

추가 편집...



## 2.3. GitHub의 추가 기능

### 2.3.1.  .gitignore

.gitignore는 개발의 편의성을 위해 대부분의 파일들은 GitHub에 업로드 하지만, 때로는 API 키나 기타 개인 정보등 민감한 정보들은 온라인에 함부로 올라가는 것을 개발자들은 원하지 않을 것이다. 그래서 제공하는 옵션(?)이 .gitignore라고 할 수 있다. 이 파일은 텍스트 파일인데, 특이한 것이 이 파일에 파일의 이름이 명기되면 git에 의해 추적 받지 않는다. 이를 통해 민감한 정보에 대해 편하게 관리할 수 있다. 너무 좋은 이 파일은 결점이 없을 것 같지만, 한 가지 주의해야할 것이 있는데 .gitignore는 GitHub에 업로드할 때 설정을 확정 짓는 것이기 때문에 `git pull`이나 `git clone`을 통해 파일을 내려받으면 기존에 작성해둔 설정 값이 사라져버릴 수 있다(대참사...). 그러므로 이미 명령어를 입력했어도 수정할 수 있는 다른 git 명령어들과 다르게 주의를 기울여야 한다. 그래서 .gitignore 파일은 같은 팀인 개발자끼리는 서로 `무조건` 자세하게 공유해야 한다.



![gitignore image](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRKHqxGa8nkdd3T1lK88h5u1R5XuW4SPxai_A&usqp=CAU)



### 2.3.2. README.md

`.md` 확장자를 가지는 파일은 마크다운 파일로 지금 작성하고 있는 이 문서 또한 마크다운 문서이다. 이 문서는 aka 블로그나 MS사의 words와 같이 텍스트를 편집하고 꾸밀 수 있는 태그들을 지원하는데 그중에서 `README.md`라고 되어 있는 마크다운 파일은 해당 깃 허브 폴더에서 미리보기로 바로 보이게 된다. 그래서 어떤 프로젝트의 개요나 오픈 소스 라이브러리의 기능을 글로 설명할 때 많이 사용한다.




# 3. Git에서 발생할 수 있는 문제상황들



`2.3.1. git init` 카테고리에서 `git init`을 사용하면서 주의해야 할 상황을 한 가지 설명했었는데, 이 챕터에서는 Git에서 발생할 수 있는 문제상황과 Git과 GitHub에서 발생할 수 있는 여러 문제 상황을 다뤄보고자 한다.



## 3.1. 이미 git init을 한 폴더 아래의 자식(Sub) 폴더에 또 git init을 하는 경우

> ` git init` 이라는 명령어 자체는 초기에 1회만 사용하는 명령어이고, 이것을 하위 디렉토리에서 사용할 수 없도록 막혀있진 않지만 하위 디렉토리에 또다시 git init을 할 경우 `Sub Module Issue`로 인해 문제가 발생할 수 있다.



## 3.2. etc...

> 추후 공부하면서 채워나갈 예정







