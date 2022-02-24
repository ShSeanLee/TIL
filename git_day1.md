# CLI(Command Line Interface)

- 홈폴더에서 우클릭 Git Bash로 열기(~ 홈폴더 표시)

- 커맨드라인 명령어

  ```bash
  # 디렉토리 생성
  mkdir 폴더명
  # 디렉토리 이동
  cd 경로 ./ or 다음경로/그다음경로
  # 파일 생성
  touch 파일명.확장자
  # 디렉토리 안 리스트를 확인(list segments)
  ls
  # 제거
  rm
  ## -r 옵션: 재귀적
  ## -rf 옵션: 강제 삭제
  # 이동/이름변경
  mv 대상파일 이동위치
  ## 이동위치가 없으면 파일이름으로 바뀜
  # 현재 나의 경로 확인(present working directory)
  pwd
  # 폴더, 파일을 여는 명령어
  start 폴더명 or 파일명
  ```

# 마크다운(Mark Down)	

- Typora 활용
- 마크다운의 문법

1. 제목 : \# 6단계 까지 가능
2. 순서가 없는 목록 : \-, \*, \+ (tab, shift+tab 사용 가능)
3. 순서가 있는 목록 : 1. 2. 3. 등
4. 강조 : *, _ 한개로 묶으면 기울임, 두개로 묶으면 굵게, ~두개로 묶으면 취소
5. 코드 : 백틱(\`)한개로 감싸서 한줄코드 가능, 백틱세개 코드종류(ex) python) 등으로 코드블럭
6. 링크 :  \[표시할글자]\(이동할주소)
7. 이미지 : \!\[대체 텍스트](이미지주소)
8. 인용 : >개수에 따라 
9. 표 : ctrl+T로 생성가능 
10. 수평선 : \- 나 \* 을 세개 써서 가능
11. ctrl+/으로 소스코드 확인가능

# git 기초

- git의 3공간(Working Directory, Staging Area, Repository)
- ![git의 3공간](git_day1.assets/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fc86c667a-616f-45b6-892e-15da6a3c494e%2FUntitled.png)

```bash
# 파일생성
touch a.txt
# 현재 디렉토리의 파일들을 git이 관리한다. (git의 repository로 관리) Master라고 뜨는지 확인.
# 맨처음 1회 & 절대 홈폴더에서 하지 않아야! 또한 그 하위폴더에서 또 init하지 않음.
git init 
# 현재 상태 확인
git status
# Staging area에 추가
git add a.txt
chages to be commited 나옴
# commit
git commit -m "문구"
# 커밋의 내역을 봄 (--oneline 옵션으로 한줄 출력)
git log

# please tell me who you are. 계정설정하기
git config --global user.name "이름"
git config --global user.email "이메일"
# 계정확인
git config -list
```

