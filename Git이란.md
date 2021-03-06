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

> 2020년 StackOverFlow에서 실시한 설문조사에 따르면 GitHub는 1위를 차지하고 있다.

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

>  [LINUX 명령어들.md](https://github.com/1-Hee/TIL/blob/master/LINUX%20%EB%AA%85%EB%A0%B9%EC%96%B4%EB%93%A4.md)

## 2.2. Git의 명령어들

### 2.2.1. git init

 git init은 git에 의해 버전관리를 받지 않는` local directory ` 중에서 개발자(사용자)가 이제부터 해당 local directory는 git으로 버전관리를 하겠다고  선언하는 과정이라고 설명할 수 있다.

```
DESKTOP MINGW64 /d/.gitTest
$ git init
Initialized empty Git repository in D:/.gitTest/.git/
```

 그래서, git init은 사용할 때 두 가지를 주의하여 사용한다. 첫째, git을 통해 버전관리 하겠음을 ‘선언’하는 것이므로 최초 1회만 사용해야한다. 둘째, 가급적 `Home directory`에는 `git init`하는 것을 삼가야한다. 두 번째 조건을 주의해야하는 이유는 홈 디렉토리에 `git init` 할 경우, 버전 관리시 온갖 잡다한 것들이 다 관리될 수 있기 때문이다 (비효율적, 비합리적).

### 2.2.2. git add

 `git add`는 working directory에 있는 파일이나 폴더를 git repository에 올리기 전 단계인 staging area에 올려 놓는 명령어이다. 

```
DESKTOP MINGW64 /d/.gitTest (master)
$ git add .

DESKTOP MINGW64 /d/.gitTest (master)
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   a.txt
```

>  `🤔 git은 왜 바로 git repository에 올리지 않는 것일까?`

 git의 `staging area`는 단순히 임시로 파일을 올려두는 저장소가 아니다. `staging area`는 `working directory`에서 `git repository` 에 업데이트 하고 싶은 파일이나 폴더를 선별해서 올릴 수 있게 하며, 유사시 잘못 올라간 파일은 취소시키고 `git repository` 에 업데이트 하기 전에 파일이나 폴더에 이상이 없는지 확인할 수 있게 하는 중간 점검을 할 수 있게 하는 공간이다. 그렇기에 `staging area`는 git에서 중요한 단계이며 꼭 필요한 것이라고 할 수 있다.

### 2.2.3. git commit –m

git은 `git commit –m` 이라는 명령어를 통해 변경 이력의 특이사항을 메모할 수 있게 한다. `메모` 라는 단어에서 선택 옵션인가 하고 생각할 수 있겠지만, 이는 개발자로 협업하는 데에는 `필수` 옵션이다. git을 통해 버전을 관리할 때, 가장 쉽고 간편하고 빠르게 파일의 변경이력을 확인하고 점검하는데에는 git의 **commit message**를 확인하기 때문이다. 그래서 예컨대 날짜를 메시지로 적는다던가, 업데이트 내역과 무관한 내용을 적는 것은 지양해야한다. (그래도 굳이 적는다면 git이 막지는 않겠지만 나중에 log로 다 남는다.)

```
DESKTOP MINGW64 /d/.gitTest (master)
$ git commit
```

```
# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# On branch master
#
# Initial commit
#
# Changes to be committed:
#       new file:   a.txt
#
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
<g Study/6. ssafy/gitTest/.git/COMMIT_EDITMSG [unix] (07:48 16/07/2022)1,0-1 All
<amming Study/gitTest/.git/COMMIT_EDITMSG" [unix] 11L, 227B
```

> ▲ `git commit –m` 양식을 지키지 않았을 때 자동으로 호출되는 Vim 화면.
> git은 커밋 메시지를 작성하는 것을 ‘강제’하고 있기 때문에 위와 같은 화면이 등장한다.

```
root
# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# On branch master
#
# Initial commit
#
# Changes to be committed:
#       new file:   a.txt
#
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
< Study/gitTest/.git/COMMIT_EDITMSG[+] [unix] (07:48 16/07/2022)1,4 All
:wq
```

> **INSERT 모드**로 커밋 메세지를 입력하고, `ESC` 키를 누른 후 명령어 `:wq`를 입력하면 미로(?)에서 탈출 가능하다.

이때 탈출하는 방법은 ‘커밋메세지 작성’하는 것이다. 이 화면에서 커밋 메시지 작성하는 방법은

1. 키보드의 `I` 키를 눌러서 **INSERT 모드** 로 전환한다. (창 아래에 명기됨)
2. 메모장에 타자 치듯이 메모를 적는다 (창 상단에 입력됨)
3. 키보드의 `ESC` 키를 눌러서 **명령어 모드** 로 전환한다.
4. 명령어 `:wq`를 입력하고 엔터를 누르면 원래의 **git bash** 화면으로 전환된다.

```
DESKTOP MINGW64 /d/.gitTest (master)
$ git commit
[master (root-commit) 8fe2cd1] root
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 a.txt
```

### 2.2.4. git status

 현재 디렉토리에서의 git의 현재상태를 알려주는 명령어이다. 다른 명령어 사진을 보면 중간중간 `git status`가 입력된 것을 볼 수 있는데, git status는 이처럼 git의 각 중간 단계에서 현재 상태를 점검하는 데 쓰이는 명령어이기에 자주 사용되었다.

```
DESKTOP MINGW64 /d/.gitTest (master)
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   a.txt

no changes added to commit (use "git add" and/or "git commit -a")

DESKTOP MINGW64 /d/.gitTest (master)
```

> `git status` 명령어를 입력하면 단계별 진행상황을 확인 가능하다. 위의 코드 블럭은 파일을 수정한 뒤 `git status`를 입력한 결과이다. `git status`는 stage와 stage의 진행 상황 별로 다른 결과 코드를 보여준다.

### 2.2.5. git log

이 명령어는 조금 특별하다(?). 바로 앞 `git status`와 다르게 **git workflow**가 **repository**에 도달하면 쓸 수 있기 때문이다. 이 명령어는 최소 1회 **commit이 일어난 경우** 에만 사용 가능하며 최근에 업데이트된 ‘변경이력’을 보여준다.

```
DESKTOP MINGW64 /d/.gitTest (master)
$ git log
commit 8fe2cd1eb5d5998ec077fca24dafaef9afd426b0 (HEAD -> master)
Author: 1-Hee <onehee9710@gmail.com>
Date:   Sat Jul 16 07:48:07 2022 +0900

    root
```

 또한, 노란색 글씨로 알 수 없는 영어와 숫자가 합쳐진 문자열을 보여주는데, 이것은 해당 `repository`의 `해쉬값`이며 고유하다 (컴퓨터마다 다르다). 이 ‘해쉬값’은 해당 repository에서 과거의 파일을 보거나 할 때 사용할 **key value** 로써 사용한다. 하지만 주의할 것은 이 행위는 ‘ROLLBACK’시킨다는 의미가 아니다.

### 2.2.6. git log --oneline

 `2.3.5. git log`를 참조하면, `git log` 라는 명령어는 다소(?) 상세한 정보들을 표시해준다. 그런데, Git은 버전관리 프로그램이기 때문에 당연히 해당 폴더에서 작업을 하면 할 수록 시간의 흐름과 함께 점점 `commit` 내역들이 쌓여갈 것이다. 만약 이 상황에 대해 어떤 해결책이 없다면 개발자들은 개발을 시작한지 오래된 폴더에서 `git pull`을 하고 `git log` 를 찍으면 고작 한 줄짜리 명령어가 자칫하면 수십, 수백 줄의 결과 코드를 반환할 수 있으니 항상 걱정이 가득해야 할지도 모르겠다. 하지만 다행히 똑똑한 개발자들은 그렇게 해두지 않았다. git log의 코드가 누적되어 양이 많아지면 다음과 같은 화면을 볼 수 있다.

```
DESKTOP MINGW64 /d/.gitTest (master)
$ git log
commit e6470c71eaaf4ac96ff4674076068382a7af76c2 (HEAD -> master)
Author: 1-Hee <email@adress.com>
Date:   Sat Jul 16 07:54:14 2022 +0900

    test2

commit ccdd7ae9d835f6def86aee23393b057c511cc2ae
Author: 1-Hee <email@adress.com>
Date:   Sat Jul 16 07:54:00 2022 +0900

    test2

commit c44e7cd1156a2eb185b27a9496aa363045635698
Author: 1-Hee <email@adress.com>
Date:   Sat Jul 16 07:53:51 2022 +0900

    test2

commit 8ea15ff2c7330e8fdc9ede22398bdc20c4d2cd26
Author: 1-Hee <email@adress.com>
Date:   Sat Jul 16 07:53:43 2022 +0900

    test2

commit ea5925de510cb7bba5daf54bdef62df3be764d80
:
```

> log의 길이가 길어져서 Vim 처럼 무시무시한(?) 콜론(:)이 등장해버린 모습이다.

 코드가 길어지면 위의 이미지와 같이 log 내역이 전부다 나타나지 않는다. 저 화면에서는 콘솔창이 마치 먹통(?)이된 것 같은 상황이 발생하는데, 이때에는 어떤 입력이나 스크롤도 맘대로 되지 않아서 패닉에 빠질 수 있다. 이때에도 **Vim 에디터** 에서 했던 것처럼 `wq` 를 입력하면 빠져나올 수 있다.

```
commit ea5925de510cb7bba5daf54bdef62df3be764d80

DESKTOP MINGW64 /d/.gitTest (master)
$
```

> `wq` 명령어를 정상적으로 입력하면 위와 같이 잘 빠져나오는 것을 확인할 수 있다.

`wq` 명렁어를 사용해서 위와 같이 성공적으로 빠져나올 수도 있지만, 그런 상황을 떠나서 log가 많이 중첩되면 한눈에 정보를 파악하기 어려워질 수 있다. 그래서 간략히 해쉬 값과 commit message를 확인할 수 있는 명령어도 존재하는데 그것이 바로 `git log --oneline`이다. 이 명령어를 입력하면 아래와 같이 간략하게 정보를 표시해주어 보기 한결 더 쉬워진다.

```
WONHEE JO@DESKTOP-C9L1NBB MINGW64 /d/.Programming Study/6. ssafy/gitTest (master)
$ git log --oneline
e6470c7 (HEAD -> master) test2
ccdd7ae test2
c44e7cd test2
8ea15ff test2
ea5925d test1
8fe2cd1 root
```

> `git log --oneline`을 입력했을 때는 무시무시한(?) 화면은 나타나지 않고, 해쉬값과 커밋메세지만 간략히 나타났다.

### 2.2.7. git checkout 해쉬값

 그동안 `git add` , `git commit - m` , `git push origin master` 등을 잘 사용했고, `git log`를 입력해서 `commit` 내역을 확인하는 것까지 순조로웠다면 아래와 같은 의문이 들 수 있을 것 같다.

>  git이 버전관리를 한다는데, 도대체 어떻게 버전관리로 한다는 거지? 어떻게 버전별로 접근을 하는 걸까?

위의 질문에 대한 해답은 바로 여기서 얻을 수 있다. 바로 git의 **해쉬값** 을 통해서 지난 버전들에 접근하고 관리할 수 있다. local에서 `git commit -m` 을 통해 변경 이력을 저장했다면, 그 이력은 고유한 값인 **해쉬값**을 가진다. 이 해쉬 값은 컴퓨터마다 전혀 다르고 '고유'하기 때문에 겹칠 수가 없다. 그래서 이 값을 기준으로 해당 폴더나 파일의 버전 관리를 할 수 있게 된다.

```
DESKTOP MINGW64 /d/.gitTest (master)
$ git checkout ea5925d
Note: switching to 'ea5925d'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at ea5925d test1

DESKTOP MINGW64 /d/.gitTest ((ea5925d...)) # ←여기 값이 달라짐
```

> git checkout 해쉬값을 입력했을 때 볼 수 있는 git bash 창이다. 컴퓨터 디렉토리 우측 괄호의 값이 변했다.

 `git checkout 해쉬값` 은 위의 사진과 같이 과거의 파일을 접근할 수 있게 해주며, 현재 파일에 스크린 샷으로 담지 않았지만, 특정 해쉬값을 입력하면 그 해쉬값에 해당하는 변경이력 까지 파일을 복원한다. (미래의 이력은 안보이게 해줌) 이때 유의할 것은 이 명령어가 그동안의 `commit` 이력을 `ROLLBACK`하는 것이 아니라는 점이다. `git checkout` 이후 현재 상태로 돌아오고 싶다면 `git checkout <branch>`를 해주면 된다. 홀로 하는 개인 프로젝트라면 `git checkout master`를 입력하면 대부분 원래의 경로로 돌아온다(아니라면 현재 branch 확인 필요).

### 2.2.8.  git rm --cached

 git에 업로드를 하다 보면, 파일을 잘못 올려버린 경우가 생길 수 있다. `git add`를 사용하면 파일은 곧바로 `staging area`에 올라가는 것이지 곧바로 `repository`에 올라가는 것이 아니기 때문에 잘못 올라간 파일을 취소 시킬 수 있다. 여기서 다시한번 `staing area`의 진가가 발휘하는 대목인 것 같다.

```
DESKTOP MINGW64 /d/.gitTest (master)
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   b.txt
```

` git add`를 입력하고 bash 창을 확인하면 위와 같은 결과 코드를 볼 수 있다. 이때 git은 친절하게 파일을 올렸다는 '정보'와 잘못 올린 경우를 대비하여 취소하는 명령어를 같이 안내해주는데, 잘못 올린 파일을 취소하는 명령어가 바로 `git rm --cached ` 이다. 이 명령어 뒤에 삭제하고 싶은 파일명을 입력하면 add된 것이 취소된다.

### 2.2.9. git commit --amend

  git에서 commit을 한 뒤에 갑자기 내가 작성한 commit message가 마음에 안들 수 있다. 그렇다면 이것을 수정하려면 새롭게 수정해서 또 commit을 해야할까? 정답은 아니다. git에서는 이러한 상황에 대비하여 commit이 된 이후라도 메세지를 수정할 수 있는 명령어를 제공하며 그것이 바로 `git commit --amend` 이다. 단, 이때 주의할 것은 이 명령어를 쓰면 무조건 Vim 편집기가 나타나게 되는데, 사용법은 위 챕터 중 `2.2.3. git commit –m`에서 설명한 것을 따라하면 되므로 당황하지 않고 메세지 편집 후 빠져나와주면 쉽게 메세지를 편집할 수 있다.

```
WONHEE JO@DESKTOP-C9L1NBB MINGW64 /d/.Programming Study/6. ssafy/gitTest (master)
$ git commit --amend
```

> `git commit --amend` 명령어를 위와 같이 입력하면 최근의 commit 내역에 대한 Vim 편집기가 뜬다.

```
test2

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# Date:      Sat Jul 16 07:54:14 2022 +0900
#
# On branch master
# Changes to be committed:
#       modified:   a.txt
#
~
~
~
~
~
~
~
~
~
~
~
~
~
D:/.gitTest/.git/COMMIT_EDITMSG [unix] (08:09 16/07/2022)                         1,1 All
"D:/.gitTest/.git/COMMIT_EDITMSG" [unix] 11L, 258B
```

> `2.3.3. git commit –m` 챕터에서 다룬 Vim 에디터  코드이다. `git commit --amend`를 입력하면 직전 커밋 내역에 대한 Vim 에디터가 활성화 된다. 여기서도 똑같이 `I` 키를 눌러서 **INSERT 모드**로 전환하고 메세지를 편집한 후 `ESC` 키를 눌러서 **명령어 모드**로 전환한 뒤 `:wq` 명령어를 입력하면 기존 디렉토리로 돌아온다.

### 2.2.10. git config

 `GitHub`에서는 사용자의 이름과 이메일 계정을 기준으로 `GitHub`에 잔디를 심는다. 이외에도 제한된 `repository`에 접근 가능 여부를 결정 하는데에도 이와 같은 정보를 사용한다. 그러므로 늘 같은 컴퓨터에서만 작업하는 게 아니라면 계정 정보 등을 체크해보는 것을 권장한다. 사용자 이름(`user.name`)과 계정(`user.email`)에 대한 명령어들은 아래와 같다.

##### git 계정 설정(한번도 설정하지 않은 경우 or 초기화한 경우)

```git
git config --global user.name "USER_NAME"
git config --global user.email "USER@EMAIL.COM"
```

> git 환경에서의 사용자 이름과 계정을 설정하는 명령어이다.

여기서 `--global` 옵션은 git 환경에서 전역으로 사용하겠음을 의미하는 것으로, 세부 파일에서만 통용되는 계정을 설정하고 싶다면 아래와 같이 `--global`  옵션을 제거하고 사용해도 된다. (이 때에는 전역으로 사용 x..)

```git
git config user.name USER_NAME
git config user.email "USER@EMAIL.COM"
```

##### git 계정 삭제

```git
git config --unset --global user.name
git config --unset --global user.email
```

여기서도 마찬가지로 `--global` 옵션을 빼면 특정 폴더 안에서의 설정을 삭제하는 용도로 사용 가능하다.

##### 실수로 계정이 여러개 등록된 경우

> `git config --global user.name` 명령어를 오타냈거나 문법을 틀린 경우 이상한 값으로 계정설정이 되는 경우가 있다. 이 때에는 기존의 설정 값들을 한방에 삭제하면 해결할 수 있다.

```git
git config --unset-all user.name
git config --unset-all user.email


// 전역 설정을 삭제하고 싶다면!
git config --unset-all --global user.name
git config --unset-all --global user.email
```

##### 계정이 1개만 잘 등록 되고, 그 계정을 삭제하고 싶은 경우

```git
git config --unset user.name
git config --unset user.email
```

##### 계정을 삭제, 추가, 편집 등을 한 뒤 잘 되었는지 확인하고 싶은 경우

```git
git config --global --list
```

### 

### 2.2.11. git remote add origin \<git hub repo adress\>

 로컬 repository에서 git commit이 끝났다면, 이제는 GitHub와 같은 서비스를 이용해 프로젝트를 온라인으로 업로드 할 차례이다. 그렇다면 이제 한 가지 의문이 떠오를 수 있다. `로컬에 있는 내 git 폴더를 어떻게 업로드하지?` 당연하게도 이 또한 명령어가 있다. GitHub에 회원가입 후 나의 계정에 귀속된 **Repository**를 만들면 아래와 같은 페이지를 볼 수 있다. GitHub는 이 페이지에서 친절하게(?)  어떻게 연결할지 가이드라인을 바로 보여주고 있다.

![0715s8](https://github.com/1-Hee/TIL/blob/master/source/0715s8.PNG?raw=true)

> GitHub에서 처음 repository를 생성하면 볼 수 있는 화면이다. 나는 분명 폴더를 만들었는데, 이 화면이 나와서 당황했다면 걱정할 필요 없다 잘 만든 것이다. GitHub는 repository 생성 후 다음 step을 헷갈려할 개발자들을 위해 친절하게 앞으로 어떤 명령어를 입력하는게 필요할지 위의 사진처럼 안내하고 있다.

### 2.2.12. git remote -v

>  GitHub와 Local의 Bridge를 확인하는 방법

`2.2.10. git remote add origin <git hub repo adress>`의 명령어를 입력하지 않았다면, 당연히 GitHub와 Local Git 저장소 사이에의 연결은 이루어지지 않는다(요청하지 않았는데 연결되는 것도 좀 이상할 것 같다). 그래서 내가 GitHub에 잘 연결했는지 확인할 수 있는 명령어가 ` git remote -v` 이다. 아래의 두 블럭에 각각 정상적으로 잘 연결되었을 때와 명령어를 입력하지 않았을 때의 결과창을 옮겨두었다.

```
DESKTOP MINGW64 /d/.test (master)
$ git remote -v
origin  https://github.com/사용자명/레포지토리.git (fetch)
origin  https://github.com/사용자명/레포지토리.git (push)
```

> 정상적으로 GitHub와 연결되어 fetch와 push 정보가 잘 나타나는 결과창이다.

```
DESKTOP MINGW64 /d/.test (master)
$ git remote -v

DESKTOP MINGW64 /d/.test (master)
```

> GitHub에서 repository를 생성한 뒤 `git remote add origin <git hub repo address>`를 입력하지 않아서 아무런 정보도 나타나지 않는 모습이다.

### 2.2.13. git clone

 Git은 개발자들 사이에 서로 협업하기 위한 **Tool** 이고 GitHub는 개발자들 사이에 서로 협업할 수 있도록 '온라인' 상으로 파일 업로드 및 다운로드를 가능하게 하는 편의를 제공하는 **서비스(Service)**이다. 그래서 GitHub에 어떤 프로젝트 폴더가 업로드 되어 있다면, 최초 생성한 사람 뿐만 아니라 나중에 합류하는 다른 사람도 참여할 수 있다. 이 때 다른 개발자의 로컬(Local) 컴퓨터 디렉토리에 프로젝트 폴더를 다운로드 하게 해주는 명령어가 `git clone`이다.  

```
DESKTOP MINGW64 ~/Desktop (master)
$ git clone https://github.com/1-Hee/Test.git
Cloning into 'Test'...
remote: Enumerating objects: 21, done.
remote: Counting objects: 100% (21/21), done.
remote: Compressing objects: 100% (7/7), done.
remote: Total 21 (delta 0), reused 21 (delta 0), pack-reused 0
Receiving objects: 100% (21/21), done.

DESKTOP MINGW64 ~/Desktop (master)
```

> git bash 창에서 GitHub의 repository의 주소를 복사해 `git clone <address>` 명령어를 입력해주면 다른 컴퓨터에서도 얼마든지 파일을 다운로드 할 수 있다. 단, 깃 주소만 알면 누구나 무분별하게 다운로드 하는 것을 막기 위해 GitHub에서는 타인이 나의 repsitory를 clone하고자 한다면 계정정보나 토큰을 요구한다.

### 2.2.14. git pull (origin \<branch\>)

`git pull (origin <branch>)`명령어는 이미 `git clone`을 통해 repository를 다운로드 한 후에 다른 개발자라던가 다른 곳에서 개발했던 내역을 나의 개인 노트북이나 데스크톱에서도 업데이트해주어 싱크를 맞출 수 있게 해주는 명령어이다.

```
DESKTOP MINGW64 /d/.gitTest (master)
$ git pull origin master
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), 656 bytes | 24.00 KiB/s, done.
From https://github.com/1-Hee/Test
 * branch            master     -> FETCH_HEAD
   796f513..7e72368  master     -> origin/master
Updating 796f513..7e72368
Fast-forward
 a.txt | 1 +
 1 file changed, 1 insertion(+)

DESKTOP MINGW64 /d/.gitTest (master)
```

> `git pull origin <branch>` 명령어를 통해 업데이트 내역을 다운받은 결과를 보여주는 bash창이다.

 명령어 뒤에 ()를 붙인 이유는 그 뒤 부분은 적지 않아도 branch가 무엇인지 알 수 있는 경우(e.g. branch가 master 1가지인 경우) 에는 git이 알아서 해당 branch에서 데이터를 다운로드하기에 생략이 가능해서이다. 만약 GitHub를 처음 다루거나 익숙치 않을 경우에는 ❗ **가급적** `git pull origin <branch>` 전체를 다 입력하길 강력 추천한다(여러 명이 협업하는 repository에서는 이상한 branch로 뒤집어 쓴다던가 하는 대참사 발생 가능).

## 2.3. GitHub의 추가 옵션

### 2.3.1.  .gitignore

.gitignore는 개발의 편의성을 위해 대부분의 파일들은 GitHub에 업로드 하지만, 때로는 API 키나 기타 개인 정보등 민감한 정보들은 온라인에 함부로 올라가는 것을 개발자들은 원하지 않을 것이다. 그래서 제공하는 옵션(?)이 .gitignore라고 할 수 있다. 이 파일은 텍스트 파일인데, 특이한 것이 이 파일에 파일의 이름이 명기되면 git에 의해 추적 받지 않는다. 이를 통해 민감한 정보에 대해 편하게 관리할 수 있다. 너무 좋은 이 파일은 결점이 없을 것 같지만, 한 가지 주의해야할 것이 있는데 .gitignore는 GitHub에 업로드할 때 설정을 확정 짓는 것이기 때문에 `git pull`이나 `git clone`을 통해 파일을 내려받으면 기존에 작성해둔 설정 값이 사라져버릴 수 있다(대참사...). 그러므로 이미 명령어를 입력했어도 수정할 수 있는 다른 git 명령어들과 다르게 주의를 기울여야 한다. 그래서 .gitignore 파일은 같은 팀인 개발자끼리는 서로 `무조건` 자세하게 공유해야 한다.

![gitignore image](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRKHqxGa8nkdd3T1lK88h5u1R5XuW4SPxai_A&usqp=CAU)

### 2.3.2. README.md

`.md` 확장자를 가지는 파일은 마크다운 파일로 지금 작성하고 있는 이 문서 또한 마크다운 문서이다. 이 문서는 aka 블로그나 MS사의 words와 같이 텍스트를 편집하고 꾸밀 수 있는 태그들을 지원하는데 그중에서 `README.md`라고 되어 있는 마크다운 파일은 해당 깃 허브 폴더에서 미리보기로 바로 보이게 된다. 그래서 어떤 프로젝트의 개요나 오픈 소스 라이브러리의 기능을 글로 설명할 때 많이 사용한다.

# 3. Git에서 발생할 수 있는 문제상황들

`2.3.1. git init` 카테고리에서 `git init`을 사용하면서 주의해야 할 상황을 한 가지 설명했었는데, 이 챕터에서는 Git에서 발생할 수 있는 문제상황과 Git과 GitHub에서 발생할 수 있는 여러 문제 상황을 다뤄보고자 한다.

## 3.1. 이미 git init을 한 폴더 아래의 자식(Sub) 폴더에 또 git init을 하는 경우

> ` git init` 이라는 명령어 자체는 초기에 1회만 사용하는 명령어이고, 이것을 하위 디렉토리에서 사용할 수 없도록 막혀있진 않지만 하위 디렉토리에 또다시 git init을 할 경우 `Sub Module Issue`로 인해 문제가 발생할 수 있다.

## 3.2. Collision

 어떤 프로젝트 파일을 `git init`을 통해 버전관리를 시작하고, GitHub에 정상적으로 연결한 뒤, 작업을 할 때에는 한 가지 주의해야할 부분이 생긴다. 우리는 앞서 질리도록 git에 대해서 다루었기 때문에 git은 버전관리를 하는 프로그램이라는 사실은 알고 있다. 만약 하나의 GitHub repository에서 두 명 이상의 개발자가 개발을 하다보면 서로 다른 시점에 commit을 하고 업데이트를 할 때, `GitHub에서는 이 commit 들의 순서를 어떻게 짜맞추는 걸까?` 하는 의문이 생길 수 있다. 이러한 경우 `해쉬값`이 중추적인 역할을 해서 교통정리가 가능하다. 이 상황에 대해서 조금 더 첨언을 하자면 가급적 서로 같은 시점에서 출발해 서로 다른 코드를 커밋하는 상황은 지양해야 한다. 로써는 설명이 부족할 수 있어서 이미지를 첨부하였다.

![0715s9](https://github.com/1-Hee/TIL/blob/master/source/0715s9.PNG?raw=true)

> 위 그림은 `HOME` 과 `Other Desktop`에서 `commit`한 내역의 순서가 맞지 않아 충돌이 발생한 상황이다. GitHub는 평행세계(?)를 방지하기 위해서 위와 같이 서로 다른 해쉬 값을 갖는 commit이 업로드 되면 나중에 들어온 commit 내역에 대해서 reject 하고, local 수준에서 해결하도록 한다.

git으로 `commit`을 하면 각각의 `해쉬값`은 고유하기 때문에, 생성 시점과 GitHub 업로드 시점에 따라서 전후 관계가 결정된다. git은 분산 버전관리 프로그램이 때문에, Server와 같은 `GitHub`, 최초에 git을 생성하고 관리하기 시작한 `HOME` 디렉토리, 그리고 1개 이상의 `다른 컴퓨터(Others)`에서 해쉬값의 순서 흐름이 같아야 한다. 분산버전관리를 하는 목적을 생각해보면 이것이 굉장히 당연한 이야기가 되는데, 만약 이렇게 서로 순서의 흐름이 맞지 않아 sink가 다르다면 그것은 과연 분산되어 관리된다고 할 수 있을까? 또한, 분산버전관리로 인해 하나의 요소가 `KNOCK OUT` 되더라도 `BACK UP` 하는 것이 불가능해질 수 도 있을 것이다. 그러므로 개발자가 git을 사용할 때에는 이러한 전체적인 구조와 흐름을 생각하며 사용하는 자세가 필요하다. 위처럼 `Conflict`된 상황이 발생하면, GitHub에서는 로컬 수준에서 해결할 수 있도록 가이드라인을 bash 창에 보여준다.

```
DESKTOP MINGW64 /d/.gitTest (master)
$ git push origin master
To https://github.com/1-Hee/Test.git
 ! [rejected]        master -> master (fetch first)
error: failed to push some refs to 'https://github.com/1-Hee/Test.git'      
hint: Updates were rejected because the remote contains work that you do    
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes   
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.

DESKTOP MINGW64 /d/.gitTest (master)
$
```

> 위에서 설명한 것처럼 서로 `push`한  `commit`의 값이 상이하게 되면 `conflict`가 발생하게 되고 `commit`이 `reject` 되게 된다.

### 3.2.1. CONFLICT 해결방법 ❓

GitHub에서는 `conflict` 가 발생하면 local에서 해결하도록 하는데, 네가지 단계만 거치면 해결이 가능하다.

1. `git pull origin <branch>`

2. `git add <file>`

3. `git  commit -m`

4. `git push (origin <branch>)`
   
   `Conflict` 상황이 발생하면, 위와 같이 네 가지 명령어를 입력하게 되면 해결이 가능한데, 여기서 주목할 부분은 충돌 경고를 본 이후에 `1. git pull origin <branch>` 를 하게 되면 git은 요상한(?) 텍스트를 보여준다.

```
a
b
cc
dd
hello world!
yallo
whats'up!
hello pow!
<<<<<<< HEAD
yellow pants
=======
bluehat!
>>>>>>> 4312589c2eb4e95c2bdcefd5c609a8403b060b8f
```

> `git pull origin <branch>`를 한 이후에 볼 수 있는 텍스트 이다.

위에서 <<<<< HEAD 부터 ==== 까지 해당하는 부분은 현재 Local이 commit한 부분을 보여주고, === 이후부터 >>> 4312589c... 까지는 GitHub에 다른 곳에서 올린 commit 부분을 보여준다. 특수기호로 마킹된 부분을 제외하고 나머지는 서로 같은 부분이라 특수기호로 구분되지 않았는데, 처음보는 특수기호라 당황할 수 있지만 그럴 것 없이 개발자가 직접 GitHub에게 교통정리만 해주면 상황은 정리되며 문제는 해결된다. 특수기호를 포함해서 충돌이 일어난 부분(특수기호의 시작부터 해쉬값으로 보이는 부분의 끝까지)을 편집해주고 `2. git add <file>` 부터 `4.  git push (origin <branch>)` 까지 차근차근 잘 수행해주면 충돌이 난 부분은 합쳐지고(merge) 정상적으로 GitHub에 `push`되는 것을 확인할 수 있다.

```
DESKTOP MINGW64 /d/.gitTest (master)
$ git pull origin master
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), 663 bytes | 23.00 KiB/s, done.
From https://github.com/1-Hee/Test
 * branch            master     -> FETCH_HEAD
   7e72368..4312589  master     -> origin/master
Auto-merging a.txt
CONFLICT (content): Merge conflict in a.txt
Automatic merge failed; fix conflicts and then commit the result.

DESKTOP MINGW64 /d/.gitTest (master|MERGING)
$ git add .

DESKTOP MINGW64 /d/.gitTest (master|MERGING)
$ git commit -m 'conflict'
[master b751464] conflict

DESKTOP MINGW64 /d/.gitTest (master)
$ git push origin master
Enumerating objects: 10, done.
Counting objects: 100% (10/10), done.
Delta compression using up to 12 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (6/6), 525 bytes | 525.00 KiB/s, done.
Total 6 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), done.
To https://github.com/1-Hee/Test.git
   4312589..b751464  master -> master

DESKTOP MINGW64 /d/.gitTest (master)
```

> `conflict` 발생 시 위에 명기한 명령어를 순서대로 잘 입력하였더니, GitHub에 `push`까지 정상적으로 잘 된 모습을 확인할 수 있다.



### 3. 3. Git과 CRLF 경고문구

컴퓨터가 줄바꿈을 인식하는 양식은 세 가지가 있습니다. 간혹 파이썬 파일을 업로드하다가 CRLF 경고가 뜨는 경우가 있는데, 이 때에는 LF, CR, CRLF 중에서 무엇을 택할 것인지 설정 변경을 통해 확실히 하면 해결됩니다. 해결법은 아래의 코드로 나타내었습니다.



```git
SSAFY@M805 MINGW64 ~/Desktop/new/hws (master)
$ git add .
warning: in the working copy of '03_practice/01_python/python_practice_0719_조원희.ipynb', LF will be replaced by CRLF the next time Git touches it

SSAFY@M805 MINGW64 ~/Desktop/new/hws (master)
$ git config core.autocrlf true
```

> 위의 `git config core.autocrlf true` 명령어를 통해 CRLF 이슈를 해결한 코드입니다.
