![말티즈 사진](./img/말티즈.png)
# Git이란
- 분산 버전 관리 프로그램

- CLI와 GUI
  - CUI : 그래픽을 통해 사용자와 컴퓨터가 상호작용하는 방식
  - CLI:명령어를 통해 사용자와 컴퓨터가 상호작용하는 방식←많은 서버/개발 시스템이 CLI를 통해 조작환경을 제공
  - CLI 명령어 (git bash로 열어서 해보기)
    - touch : 파일을 생성하는 명령어(ex. touch a.txt) 폴더는 만들 수 없음
    - mkdir : 폴더를 생성하는 명령어
    -  **ls** : 현재 작업 중인 디렉토리의 파일/폴더의 목록을 보여줌 *(폴더는 뒤에 슬래시가 붙음)*
    - **cd** : 현재 작업중인 디렉토리를 변경하는 명령어.*(path 경로정보를 꼭 확인하기)*
      - 하위폴더로 이동: `cd 파일명`
      - 상위폴더로 이동: `cd ..`
    - **start, open** : 폴더/파일을 여는 명령어*(Windows에서는 start, Mac에서는 open을 사용)*
      - code 파일명 : vscode가 설치되어 있으면 파일을 code로 열 수 있음. `code a.txt`
    - **rm** : 파일을 삭제하는 명령어
    - -r 옵션을 주면 폴더도 삭제 가능: `rm -rf fd`

### 절대경로와 상대경로    
- 절대경로
    - 루트 디렉토리부터 목적 지점까지 거치는 모든 경로를 전부 작성한 것
    - 윈도우 바탕화면의 절대경로 C:/Users/ssafy/Desktop
- 상대경로
    - 현재 작업하고 있는 디렉토리 기준으로 계산된 상대적 위치를 작성한 것.
    - 현재 작업하고 있는 디렉토리가 C:/Users 일 때 윈도우 바탕화면의 상대경로는 ssafy/Desktop
    - ./ : 현재 작업하고 있는 폴더
    - ../ : 현재 작업하고 있는 폴더의 부모 폴더(상위 폴더)

### Markdown

- 텍스트 기반의 가벼운 마크업(markup)언어 (*마크업:태그(tag)를 이용하여 문서의 구조를 나타내는 것)*
- 문서의 구조와 내용을 같이 쉽고 빠르게 적고자 탄생

  - 내여쓰기: shift+tab
  - Markdown문법 (typora cheet sheet 검색 : [https://support.typora.io/Markdown-Reference/](https://support.typora.io/Markdown-Reference/))
    - #, -, * > 스페이스바
    - ** **, == ==, * *: 볼드체는 ctrl+B눌러도 됨
    - - [ ] :체크리스트 만들기
    - ``` ``` 언어 : 여러줄 코드 작성
    - ` ` : 한줄 코드 작성
    - *나 - 세개 이상 입력하고 엔터누르면 가로줄 생성
    - 링크 삽입: [링크 이름을 여기에 적어주세요](url) : ctrl+클릭하면 해당 url로 이동
    - 이미지 삽입 : 링크삽입 맨 앞에 ! 하나 붙여주면 된다. 이미지는 그냥 드래그로 삽입하면 상대경로로 들어감. 마크다운에 이미지를 삽입했다면 이미지가 들어간 assets 폴더와 함께 사용해야됨.
    - ~~ ~~ : 취소선
  

# Git 기본기
- **Repository(Repo)**
    - 특정 디렉토리(폴더)를 버전 관리하는 저장소
    - remote repository(깃헙, 깃랩) , local repository(pc)가 있음
    - `git init` 명령어로 로컬 저장소를 생성 : 이 폴더안의 모든 파일이 git으로 버전관리되고 있다는 선언을 해줘야함 → (git bash에서 쓰기. 브랜치가 붙음)
    - .git 디렉토리에 버전 관리에 필요한 모든 것이 들어있음(숨긴 항목 보기)

- **README.md**
    - 프로젝트에 대한 설명 문서
    - Github프로젝트에서 가장 먼저 보는 문서
    - 일반적으로 소프트웨어와 함께 배포 : 플젝할때 readme도 함께 작성해야됨
    - 작성 형식은 따로 없으나, 일반적으로 마크다운을 이용해 작성
  
- **README.md 생성하기**
    - `touch README.md` → `start README.md`
- **커밋(commit)은 3가지 영역을 바탕으로 동작됨**
    - 📁**Working Directory** : 내가 작업하고 있는 실제 디렉토리
        - git에서는 버전관리 대상이 아니라고 뜸(untracked). 즉, 새로 추가된 파일들(붉은 색으로 표시됨)
        - git에 올라가 관리되면, trakced가 붙으며 modified됨(수정됨)
    - 📁**Staging Area** : 커밋(commit)으로 남기고 싶은, 특정 버전으로 관리하고 싶은 파일이 있는 곳. 즉, 중간 확인하는 공간
        - `git add` 명령어를 통해 working directory에서 staging area로 이동(tracked)
    - 📁**Repository** : 커밋(commit)들이 저장되는 곳
        - `git commit` 명령어를 통해 staging area에 있는 파일을 repository에 저장시킴(commit 1 commit 2..)
    - working directory에서 커밋으로 남기고 싶은 파일을 staging area에 올리고, 이를 repository에 저장시킨다. 저장되고 나면 staging area가 다시 비워진다.

- **Working Directory -> Staging Area**
  - `git add` 명령어를 통해 이동시킨다.
  - `git config` : 깃허브 계정 등록
    ```python
    git config --global user.email "you@example.com"
    git config --global user.name "Your Name"

    git config --global --list
    ```
   - `git status` git의 상태를 확인하는 명령어. 자주 치면서 확인해줘야됨.
  - `git add .` : 현재 경로의 모든 파일을 add 하는 명령어

- **Staging Area -> Repository**
  -  `git commit` 명령어를 통해 staging area에 있는 파일을 repository에 저장시킴
  - `git commit`
    - vim 상태가 될 수 있다.
    - vim 에는 2가지 모드가 있다. insert키로 모드를 왔다갔다 할 수 있음.
        - command 모드
        - edit 모드 : commit message 작성 가능
    - 나가는법 : esc 연타 이후 :wq (저장하고 나가기) , :Q! (저장하지 않고 나가기)
    - `git commit -m "커밋 메세지 입력하기"` : edit 모드 들어가지 않고 수정 가능.
    - `git commit -m'modify a.txt'` : 수정된 파일을 commit?
- `git log` : commit message 확인 가능. 가장 위에 있는 것이 최신


