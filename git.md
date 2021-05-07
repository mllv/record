# Git

git init

git config --global user.email "user@email.com" \
git config --global user.name "username"

(untracked 상태) \
git add README.md \
(staged 상태) \
git commit -m "commit message" \
(unmodified 상태) \
git push origin master

git log (커밋 목록과 커밋 아이디 확인 가능)

git checkout abcdefg (커밋 아이디 앞 7자리) \
git checkout - ('-'는 최신 커밋을 의미)

git remote add origin https://github.com/xxx/xxx.git \
git push origin master \
git clone https://github.com/xxx/xxx.git \
git clone https://github.com/xxx/xxx.git . (현재 폴더에 '.git' 생성)

git pull origin master (원격 저장소에 새로운 커밋이 있다면 로컬저장소로 받아옴)

## Branch
브랜치를 만들 때는 base 브랜치를 잘 설정해야 한다. \
checkout: 브랜치를 이동하는 명령어

## Merge
merge: 브랜치와 브랜치를 합치는 명령어(병합) \
충돌을 확인하기 위해 master 브랜치에 바로 병합하지 않고 나만 쓰는 브랜치에서 먼저 병합해 보고 문제가 없는지
확인 한다.

## Pull request
base: 병합된 커밋이 들어갈 브랜치 \
compare: 병합의 대상이 되는 브랜치, 내가 base 브랜치에 반영시키고 싶은 브랜치 \
Reviewers: 이 Pull request를 검토할 사람 \
Assignees: 이 Pull request를 담당하는 사람. 보통 자기 자신

Fetch: 원격 저장소의 새로운 이력을 로컬 저장소에 업데이트 하는 명령. Pull이 실제 코드를 내려받는 데 비해 Fetch는 그래프만 업데이트 한다.

## 둘 이상의 원격저장소로 협업하기
git remote add origin 원격 저장소 주소 \
git remote add upstream 원본 저장소 주소 \
origin: 원격 저장소 \
upstream: 원본 저장소를 지칭하는 관용적 닉네임 

## Rebase
Pull request를 보냈을 때 충돌이 난다면 두 가지 방법 선택 가능

1. 현재 커밋과 병합하고 싶은 커밋을 미리 내 브랜치에서 병합해서 병합 커밋을 만들고 이를 Pull request로 보내는 방법
  - 나의 Pull request에 불필요한 병합 커밋의 이력이 남음
2. 묵은 커밋을 방금 한 커밋처럼 이력을 조작하는 방법(Rebase)
  - 히스토리를 강제로 조작하기 때문에 Rebase는 반드시 혼자만 쓰는 브랜치에서 수행해야 함
  - 강제 푸시 이용

## Amend last commit
amend: 방금 했던 커밋을 원격 저장소 까지 푸시 했더라도 수정 가능



