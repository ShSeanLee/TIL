# Branch

- 브랜치는 나뭇가지처럼 여러 갈래로 작업공간을 나누어 독립적으로 작업할 수 있게 해줌.
- Master 브랜치에 작업하는 것 보다는 독립된 브랜치에서 작업을 하고 PR(Pull Request)를 보내는 것이 유지보수에 유리



## git branch

```bash
# 브랜치 목록 확인
$ git branch

# 원격 저장소의 브랜치 목록 확인
$ git branch -r

# 새로운 브랜치 생성
$ git branch <브랜치 이름>

# 특정 커밋 기준으로 브랜치 생성
$ git branch <브랜치 이름> <커밋 ID>

# 특정 브랜치 삭제
$ git branch -d <브랜치 이름> # 병합된 브랜치만 삭제 가능
$ git branch -D <브랜치 이름> # (주의) 강제 삭제 (병합되지 않은 브랜치도 삭제 가능)
```



## git switch

- 현재 브랜치에서 다른 브랜치로 HEAD를 이동시키는 명령어. HEAD란 현재 브랜치를 가리키는 포인터를 의미.
- 그래서 branch 목록 확인할때 HEAD가 붙어있으면 현재 있는 브랜치란 소리임.

```bash
# 다른 브랜치로 이동
$ git switch <다른 브랜치 이름>

# 브랜치를 새로 생성과 동시에 이동(create and move)
$ git switch -c <브랜치 이름>

# 특정 커밋 기준으로 브랜치 생성과 동시에 이동
$ git switch -c <브랜치 이름> <커밋 ID>
```



## git merge

- 합쳐지고 싶은  브랜치에서 합칠 브랜치로 이동(Master같은)
- git merge 합쳐질 브랜치
- 합쳐져서 빈 브랜치는 git branch -d로 지운다



### merge conflict

- master 와 다른 브랜치에서 서로 다른 부분이나 다른 파일을 수정한 다음에 병합하면 아무 문제가 생기지 않음
- but, 같은 부분을 수정한다면? Conflict 발생!
- 네 가지 선택권 중에서 1번 반영, 2번반영, 둘다반영, 비교 중 선택하고
- 저장한뒤 add, commit의 과정을 통해 merge를 반영



### + 추가사항

```bash
# master, hotfix 어디에서 commit했는지 보기위해서
git log --oneline --graph --all
		all	graph 순서 바뀌어도 같음

# 커밋간 차이 보기(해시값 : log에서 나온 번호)
git diff 해시값1 해시값2

git config --global core.editor "code --wait"
이거를 한다음에는 
commit만 쳐도 위에서 메시지를 칠 수 있음.

git config --global --list

# 에디터를 편집해서 commit만 쳐도 위에 본문에서 수정하고 저장하는것 가능.
git config --global --unset core.editor

# master에가서
git merge (브랜치명)  - master에 branch를 병합함.
```



## git workflow

- Branch를 이용해 협업하는 두가지 방법

1. 원격 저장소 소유권이 있는 경우

   	- 원격 저장소가 자신의 소유이거나 collaborator로 등록 되어 있는경우(이외에는 권한 없는것임)

   - 기능별 브랜치를 통한 구현
     - Clone > 클론한 저장소에 대한 브랜치 생성(작업할 기능별) > 작업 완료 후 Push
     - \> Pull Request(PR) > 병합된 브랜치 삭제(원격저장소의) > Pull > 로컬 브랜치 삭제

2. 원격 저장소의 소유권이 없는 경우(Fork & Pull 활용)

   - 자신의 소유가 아닌 경우

   - 작업흐름

     - Fork를 통한 내 원격 저장소에 복제 > 로컬 저장소에 복제된 내 원격저장소를  Clone > 로컬 저장소와 원본원격저장소 연결

       \>  로컬 저장소에서 작업할 브랜치 생성 > 작업 완료후 내 복제 원격 저장소(Origin)에 push 

       \> Origin의 브랜치를 upstream의 master에 반영해 달라는 PR > 병합 완료된 Origin의 브랜치 삭제 > upstream을 Pull

       \> 로컬 브랜치의 삭제