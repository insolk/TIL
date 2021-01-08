# git command

> git을 사용하기 위한 기본 명령어



## 설정

### 1. init

- `git init`
- 현재 폴더를 `git`으로 관리 하겠다. => `.git`폴더를 생성
- 최초에 한번만 실행하는 명령어



### 2. config

- `git config --global user.email "email@email.com"`
- `--global` 옵션과 `--local` 둘 중 하나 선택해서 사용
  + 일반적으로 global설정을 해놓으면 내 컴퓨터에서 추가적으로 변경할 일이 없음



### 3. status

- `git status`
- 현재 git의 상태를 출력해주는 명령어



### 4. diff

- `git diff`
- **마지막 커밋**과 **현재 폴더 상태**를 비교해서 차이점을 출력



### 5. log

- `git log`
- 커밋 히스토리를 출력



### 6. remote add

- `git remote add orgin <url>`
- 별명은 origin이고 실제주소는 <url>인 원격저장소 추가



## 저장

### 1. add

- `git add <추가하려고 하는 파일>`
  - `git add .` : 한번에 모든 파일과 모든 폴더를 add
- `working directory`에서 변경점을 `staging area`로 이동



### 2. commit

- `git commit -m "메세지"` : 한번에 메세지 까지 남김



### 3. push

- `git push orgin master`
- 원격 저장소에 master 브랜치의 데이터를 전송



### 4. pull

- `git pull origin master`
- 원격 저장소에서 커밋 가져오기
- 수정전에 pull해서 가져오는게 베스트






## 브랜치 관련



### branch

- 브랜치 목록 확인
- `git branch <브랜치명>` : 새 브랜치 생성
- `-d` : 브랜치 삭제



### checkout

- `git checkout <브랜치명>`
- 2.23이후 `switch`명령으로 바뀜



### merge

- `git merge <브랜치명>`

- 병합 원하는 더 상위 브랜치에서 스위치 후 시작
- 명령어에는 합치고 싶은 브랜치명 입력
- 병합하고 나서 기능 구현 다했으면 삭제하자
- 나중에 또 수정해야하면 지우고 다시 만들어서 수정 가능



### fork

- 남의 repo를 복사해서 내 repo처럼 만듦
- 수정한 뒤에 주인 repo에 pull request하여 소스 추가 가능