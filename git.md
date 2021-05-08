# Git
```bash
git init (Git 저장소 생성)
```
- 워킹트리(working tree): 일반적인 작업이 일어나는 곳, 커밋을 체크아웃하면 생성되면 생성되는 파일과 디렉토리
- 로컬 저장소(local repository): .git폴더(커밋, 커밋을 구성하는 객체, 스테이지가 모두 이 폴더에 저장됨)
- 작업폴더 = 워킹트리 + 로컬 저장소
- 원격 저장소(remote repository): 로컬 저장소를 업로는 하는 곳(GitHub)
- Git 저장소: 엄밀하게는 로컬 저장소를 의미하지만 넓은 의미로 작업 폴더를 의미하기도 한다

## git config
- system옵션은 PC전체의 사용자를 위한 옵션
- global옵션은 현재 사용자를 위한 옵션
- local옵션은 현재 Git 저장소에서만 유효한 옵션
- 우선순위: local > global > system

```bash
git config --global <옵션명> # 지정한 전역 옵션의 내용을 살펴봄
                    <옵션명> <새로운 값> # 지정한 전역 옵션의 값을 새로 설정
                    -unset <옵션명> # 지정한 전역 옵션을 삭제
```
```bash
git config --local <옵션명> # 지정한 지역 옵션의 내용을 살펴봄
                   <옵션명> <새로운 값> # 지정한 지역 옵션의 값을 새로 설정
                   -unset <옵션명> # 지정한 지역 옵션의 값을 삭제
```
```bash
git config --system <옵션명> # 지정한 시스템 옵션의 내용을 살펴봄
                    <옵션명> <값> # 지정한 시스템 옵션의 값을 새로 설정
                    --unset <옵션명> <값> # 지정한 시스템 옵션의 값을 삭제
```
```bash
git config --list # 현재 프로젝트의 모든 옵션을 살펴봄
```

Git 전역 옵션 설정
```bash
git config --global user.email "이메일 주소"
git config --global user.name "이름"
```
Git 기본 에디터 확인
```bash
git config core.editor
git config --global core.editor
git config --system core.editor
```

- untracked
- tracked ( staged | modified | unmodified )
---
```bash 
git add README.md (staged 상태로 바뀜)
```
```bash
git commit -m "commit message" (unmodified 상태로 바뀜)
```
```bash
git push origin master
```
---
```bash
git add 파일1 파일2 ... # 파일들을 스테이지에 추가

git commit # 스테이지에 있는 파일들을 커밋
git commit -a # add 명령을 생략하고 바로 커밋하고 싶을 때 사용(untracked 팡리은 커밋되지 않음)

git push [-u] [원격 저장소 별명] [브랜치 이름] 
# 현재 브랜치에서 새로 생성한 커밋들을 원격 저장소에 업로드
# -u: 브랜치의 업스트림을 등록할 수 있음
# 한 번 등록한 후에는 git push만 입력해도 됨

git pull 
# 원격 저장소의 변경사항을 워킹트리에 반영
# git fetch + git merge 명령과 같음

git fetch [원격 저장소의 별명] [브랜치 이름]
# 원격 저장소의 브랜치와 커밋들을 로컬 저장소와 동기화 함
# 옵션을 생략하면 모든 원격 저장소에서 모든 브랜치를 가져옴

git merge <브랜치 이름>
# 지정한 브랜치의 커밋들을 현재 브랜치 및 워킹트리에 반영함
```

## CLI로 log 살펴보기
```bash
git log 
# 커밋 목록과 커밋 아이디 확인 가능
# 커밋 아이디는 40자리의 16진수 SHA1 hash checksum

git log -n<숫자> # 전체 커밋 중에서 최신 n개의 커밋만 살펴봄

git log --oneline --graph --decorate --all
# --oneline: 커밋 메시지를 한 줄로 요약해서 보여줌
# --graph 커밋 옆에 브랜치의 흐름을 그래프로 보여줌
# --decorate: 원래는 --decorate=short 옵션을 의미, 브랜치와 태그 등의 참조를 간결하게 표시
# --all: all 옵션이 없을 경우 HEAD와 관계 없는 옵션은 보여주지 않음
```
## 좋은 커밋 메시지의 7가지 규칙
1. 제목과 본문을 빈 줄로 분리한다.
2. 제목은 50자 이내로 쓴다.
3. 제목을 영어로 쓸 경우 첫 글자는 대문자로 쓴다.
4. 제목에는 마침표를 넣지 않는다.
5. 제목을 영어로 쓸 경우 동사원형(현재형)으로 시작한다.
6. 본문을 72자 단위로 줄바꿈한다.
7. 어떻게 보다 무엇과 왜를 설명한다.

```bash
git help <명령어> # 해당 명령어의 도움말 표시
```

## 원격 저장소 관련 CLI 명령어
```bash
git remote add <원격 저장소 이름> <원격 저장소 주소>
# 원격 저장소를 등록
# 원격 저장소는 여러 개 등록할 수 있지만 같은 별명의 원격 저장소는 하나만 가질수 있음
# 통상 첫번째 원격 저장소를 origin으로 지정

git remote -v # 원격 저장소 목록
```
```bash
git push -u origin master 
# push와 동시에 upstream지정
# -u는 --set-upstream의 단축명령
# upstream은 로컬 저장소와 연결된 원격 저장소를 뜻함
```
```bash
git clone <저장소 주소> [새로운 폴더명]
# 저장소 주소에서 프로젝트를 복제
# 새로 생길 폴더명은 생략 가능
# 생략하면 프로젝트 이름과 같은 이름의 폴더가 새로 생성됨
# 저장소 주소는 꼭 원격일 필요가 없음, 로컬 저장소도 복제 가능

git clone <저장소 주소> [새로운 폴더명] . # 현재 폴더에 '.git' 생성
```

## CLI로 브랜치 생성하기
```bash
git checkout <커밋 아이디 앞 7자리 또는 커밋 아이디 전체>
git checkout - ('-'는 최신 커밋을 의미)
```
```bash
git remote add origin <원격 저장소 주소>
git push origin master
```
```bash
git pull origin master (원격 저장소에 새로운 커밋이 있다면 로컬저장소로 받아옴)
```
```bash
git status (Git 워킹트리의 상태를 보는 명령, 워킹트리가 아닌 폴더에서 싱행하면 오류 발생)
```
```bash
git status -s (git status 명령보다 짧게 요역해서 상태를 보여줌, 변경된 파일이 많을 때 유용)
```

## branch
브랜치를 만들 때는 base 브랜치를 잘 설정해야 한다. \
checkout: 브랜치를 이동하는 명령어

## merge
merge: 브랜치와 브랜치를 합치는 명령어(병합) \
충돌을 확인하기 위해 master 브랜치에 바로 병합하지 않고 나만 쓰는 브랜치에서 먼저 병합해 보고 문제가 없는지
확인 한다.

## pull request
- base: 병합된 커밋이 들어갈 브랜치 
- compare: 병합의 대상이 되는 브랜치, 내가 base 브랜치에 반영시키고 싶은 브랜치 
- reviewers: 이 pull request를 검토할 사람 
- assignees: 이 pull request를 담당하는 사람. 보통 자기 자신

fetch: 원격 저장소의 새로운 이력을 로컬 저장소에 업데이트 하는 명령. pull이 실제 코드를 내려받는 데 비해 fetch는 그래프만 업데이트 한다.

## 둘 이상의 원격저장소로 협업하기
origin: 원격 저장소
```bash
git remote add origin <원격 저장소 주소>
```
upstream: 원본 저장소를 지칭하는 관용적 닉네임
```bash
git remote add upstream <원본 저장소 주소>
```

## rebase
pull request를 보냈을 때 충돌이 난다면 두 가지 방법 선택 가능

1. 현재 커밋과 병합하고 싶은 커밋을 미리 내 브랜치에서 병합해서 병합 커밋을 만들고 이를 pull request로 보내는 방법
    - 나의 pull request에 불필요한 병합 커밋의 이력이 남음
2. 묵은 커밋을 방금 한 커밋처럼 이력을 조작하는 방법(rebase)
    - 히스토리를 강제로 조작하기 때문에 rebase는 반드시 혼자만 쓰는 브랜치에서 수행해야 함
    - 강제 push 이용 (--force-with-lease)

## amend last commit
amend: 방금 했던 커밋을 원격 저장소 까지 push 했더라도 수정 가능

## cherry-pick
커밋 하나만 떼서 다른 브랜치에 반영하고 싶을 때

## reset
```bash
git reset [파일명]...
# 스테이지 영역에 있는 파일들을 스테이지에서 내림(언스테이징)
# 워킹트리의 내용은 변경되지 않음. 옵션을 생략할 경우(= mixed reset) 스테이지의 모든 변경사항을 초기화
```

soft 
- 모든 로컬 변경사항을 유지
- 변경사항을 스테이지 위로 둬서 다시 당장 커밋할 수 있음 

mixed
- 작업 상태는 그대로 두지만 인덱스는 리셋
- 변경사항을 스테이지 아래 둬서 다시 무엇을 스테이지 위로 add 할지 고민할 수 있음 

hard
- 모든 작업 상태 내 변경사항을 버림
- 강제 push

## revert
변경사항을 되돌리고 변경사항을 되돌렸다는 이력을 남김 \
방금 한 커밋 만이 아니라, 이전에 한 커밋도 얼마든지 되돌릴 수 있음

## stash
변경사항을 잠시 서랍속에 넣어뒀다가 나중에 다시 꺼내 쓰는 방법 \
stash에는 tracked상태(한번이라도 Git에 올렸던 상태)인 파일들만 들어감


