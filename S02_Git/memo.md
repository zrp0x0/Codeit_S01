# Git을 활용한 버전 관리

---

## 개요

### 버전 관리 시스템의 필요성
- 파일이 변경되면 변경 이력을 저장할 수 있음
- 이전 버전으로 돌아갈 수 있음
- 어떤 변경 사항이 발생했는지 알아보기 쉬움
- 협업하기에 좋음
- 백업용

### 대중적인 버전 관리 시스템: Git
- Git: 소스 코드 기록을 관리하고 추적할 수 있는 버전 관리 시스템
- Github: Git Repository(저장소)를 관리할 수 있는 클라우드 기반 서비스

### Contributor
- 오픈 소스를 열람하고 수정 및 개선안 제안을 하는 사람

### Git Repository vs Local Repository
- Git Repo: 원격 온라인 서버 상의 저장소 여러 사람이 함께 공유 가능
- Local Repo: 내 컴퓨터의 저장소(개인용)

### Fork
- contributor가 되고 싶다면?
- 다른 사람의 Repo를 Fork한 후
- clone을 해서 local로 가져옴
- push를 함(다른 사람한테는 pull request)
- 합의점이 오면 pull

---

## Git이란?


### Git이란?
- **형상 관리를 위한 소프트웨어 개발에서 사용되는 분산 버전 관리 시스템**
- Distributed Version Controll System(DVCS)
    - 버전 관리: 소프트웨어의 여러 버전을 기록하고 특정 시점으로 롤백 가능
    - 변경 추적: 누가, 언제, 무엇을 변경했는지 기록
    - 협업 지원: 여러 개발자가 동시에 작업할 수 있도록 충돌을 방지함
    - 품질 보장: 체계적인 관리로 오류를 줄이고 소프트웨어의 품질을 높임

---

## Git / Github

### Git? Github?
- 일단 Git은 로컬에서 버전을 관리해주는 프로그램을 의미
- 근데 만약에 내가 만든 걸 가지고 협업을 하고 싶다면 어떻게 해야할까?
- 제일 쉬운 방법은 웹 사이트에 파일로 올리면 될 것 같음 => 웹 사이드 == Github

### 주요 명령어
- add, commit, push: 온라인 원격 저장소에 업로드하는 과정
- fork, clone: 협업자의 작업물을 나의 로컬에 다운로드하는 과정
- pull request: 상대 협업자에게 나의 작업 완성물을 취합해 달라고 요청하는 과정
- merge: 상대방의 작업물과 나의 작업물을 취합하는 과정

---

## Git의 핵심 개념

### Git의 3가지 작업 영역
- Git은 파일을 단순히 "저장"하는 것이 아니라
- 작업을 "단계별 상태"를 구분해서 관리할 수 있음
- 1. Working Directory (작업 디렉토리)
    - 사용자가 직접 파일을 수정하는 공간

- 2. Staging Area
    - 커밋할 파일을 준비하는 임시 공간
    - git add를 통해 Working Directory의 변경 사항을 올릴 수 있음

- 3. (Local) Repository
    - git commit으로 Staging Area의 파일들이 영구적인 변경 이력으로 저장되는 공간
    - 커밋은 **고유한 ID**로 식별됨

### Commit과 버전의 개념
- Commit
    - 프로젝트의 스탭샷(사진)을 찍어두는 행위
    - 그 시점의 상태를 저장하고 돌아갈 수 있음

- Commit은 의미 있는 작업 단위가 되어야함
    - 파일 하나 수정했다가 아닌, **기능 단위** 또는 **논리적 단위**로 커밋하는 것이 좋음
        - 로그인 구현
        - README 문서 수정
        - 결제 기능 구현

- Good Commit Message
    - **현재 시제**
    - **명령형**
    - ex. Fix typo in README

### HEAD의 이해
- Git에서 현재 작업 중인 위치 즉 현재 커밋(버전)을 가리키는 포인터
- Git은 HEAD를 기준으로 현재 어떤 브랜치나 커밋에서 작업중인지 확인
- HEAD는 **현재 작업중인 브랜치의 가장 마지막 커밋을 가리킴**

### 새로운 커밋의 기준점
- 지금부터 새로 작업을 시작한다는 의미
- HEAD는 꼭 브랜치만 가리키는게 아니라, 특정 커밋으로 이동할 수 있음(Detached HEAD 상태)

### HEAD를 통한 버전 간 이동
- git checkout <커밋ID>로 HEAD가 다른 커밋을 가리키도록 할 수 있음
- git reset, git revert 명령어도 HEAD의 이동 또는 되돌리기를 

---

## Git 기본 명령어 

### 초기 설정
- 전역으로 유저 정보를 저장
- 내 디바이스에서 추적되는 모든 폴더가 설정된 유저로 동일하게 적용됨
```bash
git --version # 깃 버전 확인
git config --global user.name "원하는 사용자명"
git config --global user.email "github 이메일"
```

- 특정 사용자 정보로 설정
```bash
git config user.name "원하는 사용자명"
git config user.email "github 이메일"
```

### 저장소 설정 및 초기화 및 사용
- 보통 다음과 같은 3단계를 가짐
```bash
git init
git add <파일1> <파일2>
git add . # 모든 파일 추가 가능 (gitignore에 없는)
git commit -m "커밋 메세지"
```
- git add를 통해 stage 영역에 추가할 수 있음 (아직 완전한 저장은 아님)
- git commit을 통해 local repo로 추가할 수 있음 (완전한 저장)

```bash
git status # 커밋 직전 체크하는 용도로 확인 / 어떤 파일이 스테이징되어 있는지 확인 가능
```

### 변경 사항 되돌리기
- 작업 디렉토리 파일을 스테이징(또는 HEAD)의 상태로 되돌림
- **주의**: 스테이징으로 추가한 이후 작업한 내용이 이전의 내용으로 덮어씌워질 수 있음
```bash
echo "Hello" > hello.txt
git add hello.txt # 스테이징 영역에 올라가있음
echo "Bye" > hello.txt # 작업 디렉토리에서 수정함
git restore hello.txt # 스테이징 영역에 올라가있던 hello.txt 내용으로 "Bye"가 "Hello"로 다시 바뀜
```

### 스테이징 취소
```bash
git restore --staged hello.txt # 스테이징 취소
```
- 주의: 파일 내용은 그대로이며, 스테이징에서만 제외됨
    - 이게 무슨 말이냐면 아까처럼 롤백되는게 아니라 그냥 해당 파일의 스테이징 기록이 날아감

---

## 정보 확인하기

### 상태 확인
```bash
git status
```

### 커밋 히스토리 보기
```bash
git log
git log --oneline # 한 줄로 보여줌
git log -p # patch 형식으로 보여줌
```

### 변경 사항 비교
```bash
git diff
```
- 워킹 디렉토리와 스테이징 영역 사이의 변경 내용을 확인
- 즉, 아직 git add하지 않은 차이점 보기
- |이걸로 봐봐|

```bash
git diff --staged
```
- 스테이징 영역과 마지막 커밋 간의 차이 확인
- 커밋하기 직전 상태와의 비교

---

## 버전 관리하기: commit / reset

### commit
- local Repo에 올리기
```bash
git commit -m "message"
git commit -am "auto add and first commit" # 수정된 파일만 자동 스테이징 후 커밋
```
- 주의: 새로 추가된(untracked) 파일은 포함되지 않음(git add 필요)
    - 이게 무슨 말이냐면 완전히 새로운 파일을 만들면 git add를 안하면 추적하지 않음(폴더를 만들어도 안에 내용물이 있어야함)

### reset
- 이전 상태로 되돌리기
```bash
git reset --soft HEAD^  # 마지막 커밋만 취소
git reset --mixed HEAD^ # 커밋 + git add 취소
git reset --hard HEAD^  # 전체 롤백 (주의 - 작업 디렉토리도 롤백됨)
```

---

## gitignore 파일 활용
- 만들어주는 사이트 있음
- 여기에 들어있는 파일/폴더는 반영하지 않음
- 근데 이미 반영되어 있는 즉, 추적하고 있는 파일은 지워줘야함(깃허브랑 연동하고 싶을때)


-- 이거 롤백?