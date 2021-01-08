# git tip

> git 소소한 팁





## 깃 실수시 수정 방법 정리

- staging area에 있는 파일 뺴고 싶을 때
  - `git restore --staged <file>` 신형 깃
  - `git reset HEAD <file>` 구형
- unstage시키는 건 **왠만하면 하지말자**



### 커밋 되돌리기

- 커밋 수정 또한 **최대한 하지말자**
- 메세지만 수정
  - `git commit --amend`
  - 단, 마지막 최근 메세지만 수정 가능함
- 커밋 자체를 취소하기(**하기전에 신중하게 커밋하는게 중요**)
  - `git reset HEAD^`
  - ^표시의 개수에 따라 뒤로 돌리기가 가능
- `git reset` => **사용하지 말자**(커밋 기록을 아예 없애버려서 과거로 돌아감)
  - `--hard` : 변경되었던 코드까지 전부 다 삭제
  - `--soft` : 파일은 남겨줌

- `revert` : 커밋도 지워지면서 지워졌다는 기록이 남겨진다는게 `reset`과의 큰 차이점



## 깃 블랙리스트 관리

- 보안이나 필요없는 파일 `.gitignore`으로 관리
- [파일만들기](https://www.toptal.com/developers/gitignore) 링크



[깃 공식문서](https://git-scm.com/book/en/v2)