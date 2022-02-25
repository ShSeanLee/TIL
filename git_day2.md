# 2일차 정리

## github 가입 및 설정 변경

- 가입 후 Settings -> Repository에서 Default Branch를 master로 설정

- New Repository 생성

  1. TIL 폴더 생성
  2. TIL url을 복사하여

  ```bash
  $ git init
  $ git remote add origin https://~~
  				이름		주소
  $ git reomte -v 원격저장소 조회
  # 원격 저장소 연결 삭제
  $ git remote rm origin
  ```

  

- 로컬저장소에서 커밋 생성(touch, add, commit, push)

```bash
$ git add day1.md
$ git commit -m "문구"
#커밋 확인
$ git log --oneline
# if log만 했을시에는 q로 빠져나온다.

# git push <저장소 이름> <브랜치 이름>
# 보통은 		origin		master
```

- 처음 push 시에는 vscode 자격증명이 나옴. Authorize한다.

- README.md 파일 push
  - Github가 인식해서 깃허브내에 내 페이지에서 첫 화면에 보여줌.
  
  ---
  
  

## .gitignore

1. .gitignore 파일 생성
2. 쉽게 작성할 수 있는 [웹사이트](https://www.toptal.com/developers/gitignore)
3. python, jupyternotebook 등 찾아서 생성 클릭 후 긁어옴.



## clone, pull

### git clone

- 원격 저장소의 커밋 내역을 모두 가져와서, 로컬 저장소를 생성하는 명령어
- 이름을 설정하지 않으면 원격저장소에서의 이름과 똑같은 이름으로 복제됨
- git clone <주소> <이름>형태로 작성
- 현재 관리되고 있지 않은 경로에서 bash를 실행해서 복제함.
- 이 때 복제된 로컬 저장소는 이미 git init과 git remote add가 수행되어 있음.



### git pull

- 원격 저장소의 변경 사항을 가져와서, 로컬 저장소를 업데이트 하는 명령어
- 둘이 완전히 일치하면 git pull을 해도 변화가 일어나지 않음.
- git pull <저장소이름> <브랜치이름>

- git pull origin master



### git clone vs git pull

- git clone은 한번만 실행. 원격저장소를 복제해서 로컬에 저장소를 새로 만드는 것
- git pull은 동기화 하는 행위. git push의 반대방향 의미.



### Conflict

- 원격과 로컬 저장소의 커밋 내역이 다를때. Rejected (ex: 깃허브에서 수정했을때 발생)
- Rejected 뜨면 일단 Pull을 해보자.
- 같은 부분을 수정했을 때 어떻게 할지를 물어봄(선택할 수 있게)
- 선택한 후에는아직 MERGING 상태이므로 add > commit > push 순으로 실행