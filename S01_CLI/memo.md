# CLI(Command Line Interface) 사용법 익히기

---
## 개요


### CLI / IO
- CLI (Command Line Interface)는 대표적인 텍스트 기반 I/O 환경
- 개발자에게 GUI보다 강력한 작업에 도움을 줄 수 있음 
- AWS(Amazon Web Service) / GCP(Google Cloud Platform)
- 서버는 보통 Linux를 굉장히 많이 사용함
- 수업에서는 Git Bash를 사용 (POSIX 제공 - Linux Standard에 맞게 하기 위해서)



---
## 실습 01


### 명령어
- pwd: print working directory
- mkdir: make directory
- ls: list
    - ls -l: 파일 권한, 소유자, 크기, 수정 시간 등 상세히 표시 (long list)
    - ls -a: 숨김 파일(.)을 포함한 모든 파일 표시 (all)
    - ls -R: 하위 디렉토리 내용까지 재귀적으로 표시
    - ls -al | ls -la: 숨김 파일을 포함하여 상세 정보를 목록으로 표시

    - drwxrwxrwx: d: directory
    - -rwxrwxrwx: -: file

- cd: change directory: 폴더를 이동할 때 사용
- touch: 파일 생성하기
    - 이미 있는 파일이면 그 파일을 새로고침해줌(동기화)

- >: 실행 결과를 파일로 저장하기
    - ls > ls.txt: ls.txt에 ls 명령어 실행 결과가 들어감
    - echo "내가 넣을 문장" > hi.txt: hi.txt에 내가 넣을 문장이 들어감
    - 만약 파일이 없으면 파일을 먼저 생성하고 그 결과를 반영함

- cat: concatenate
    - 파일 생성: cat > [파일명]
    - 덮어 쓰기: cat > [파일명]
    - 이어 쓰기: cat >> [파일명]



---
## 실습 02


### 실습 명령어
```bash
mkdir helloWorld
cd helloWorld
mkdir hello
cd hello
pwd
mkdir bye
touch bye.
ls -al
```


### 명령어
- rm: remove: 폴더나 파일을 삭제할 때 사용함
    - rm: 단일 파일을 삭제할 수 있음
    - rm -rf: 폴더 삭제 (안에 내용물도 강제로 삭제): recursive force

- mv: move: 폴더나 파일의 이름을 변경, 또는 폴더나 파일의 위치 옮기기
    - mv [파일1] [폴더1]: 파일1을 폴더1로 이동
    - mv [파일1] [파일2]: 파일1을 파일2로 바꿈

- cp: 폴더나 파일을 복사
    - 없으면 만들고 복사함
    - 있으면 덮어씀
    - cp -rf: 폴더를 통째로 이동: 파일이나 폴더를 하위 내용까지 포함하여 강제로 복사할 때 사용하는 명령어

- cd 심화
    - cd ..: 바로 상위 폴더로 이동
    - cd /: 루트 폴더로 이동
    - cd [pwd]: pwd로 이동