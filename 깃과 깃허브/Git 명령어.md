# Git 명령어 정리

***

>## _설정 및 초기화_

### 1. `git init`
   - 새로운 Git 저장소를 초기화한다.

### 2. `git clone <repository_url>`
   - 원격 저장소를 복제한다.

### 3. `git config`
   - Git의 환경 설정을 변경합니다.
     - `git config --list`: 현재 git 설정 모두 확인
     - `git config --global user.name "Your Name"`: 사용자 이름 설정
     - `git config --global user.email "Your email"`: 사용자 이메일 설정
     - `git config --global core.autocrlf true`: Windows에서 줄 바꿈 처리를 자동으로 설정
     - `git config --global core.safecrlf false`: 줄 바꿈 처리 안전 설정(뉴라인 경고 발생 없앰)
     - `git config --global core.editor "편집기명"`: 기본 편집기 설정
     - `git config --global init.defaultBranch main`: 기본 브랜치 이름 main으로 설정
     - `git config --global alias.별칭 '이름'`: 별칭 설정
        
>## _변경 내용 확인_

### 4. `git status`
   - 현재 작업 디렉토리의 상태를 확인한다.

### 5. `git add .`
   - 모든 변경 사항을 스테이징 영역에 추가한다.

### 6. `git commit -m "Initial commit"`
   - 스테이징 영역에 추가된 내용을 커밋한다.

### 7. `git log`
   - 커밋 로그를 확인합니다.
     - `git log --oneline --graph --all`: 그래프와 브랜치 정보와 함께 간략한 형식으로 모든 커밋을 확인
     - `git log -p -2`: 최근 2개의 커밋의 변경 내용을 보여줌

### 8. `git diff`
   - 변경된 파일의 차이를 확인한다.
     - `git diff --staged`: 스테이징 영역과 최종 커밋 간의 차이 확인
     - `git diff <file>`: 특정 파일의 변경 내용 확인

>## _브랜치 관리_

### 9. `git branch`
   - 브랜치 목록을 보여준다.
     - `git branch <branch_name>`: 새로운 브랜치 생성
     - `git checkout -b <branch_name>`: 브랜치 생성 및 해당 브랜치로 전환 (Git 2.23 이상)
     - `git switch -c <branch_name>`: 브랜치 생성 및 해당 브랜치로 전환
     - `git branch -d <branch_name>`: 브랜치 삭제

### 10. `git checkout <branch_name>`
  - 특정 브랜치로 전환한다.
      - `git switch <branch_name>`: 특정 브랜치로 전환 (Git 2.23 이상)

### 11. `git merge <branch_name>`
  - 현재 브랜치에 다른 브랜치를 병합한다.
      - `git merge --ff <branch_name>`: Fast-Forward 병합 수행
      - `git merge --no-ff <branch_name>`: 일반적인 3-way 병합 수행

### 12. `git rebase <branch_name>`
  - 현재 브랜치를 대상 브랜치로 리베이스한다.

### 13. `git reset`
  - 커밋을 취소하거나 스테이징 영역을 초기화한다.
      - `git reset --soft HEAD^`: 최근 커밋을 취소하고 변경 사항을 스테이징 영역에 유지
      - `git reset --hard HEAD^`: 최근 커밋을 취소하고 변경 사항을 모두 삭제

### 14. `git revert <commit_hash>`
  - 특정 커밋을 되돌린다.

### 15. `git cherry-pick <commit_hash>`
  - 특정 커밋을 현재 브랜치로 가져온온다.

>## _원격 저장소 관리_

### 16. `git remote`
  - 원격 저장소를 관리한다.
      - `git remote -v`: 원격 저장소의 URL을 확인

### 17. `git push`
   - 로컬 변경 사항을 원격 저장소로 푸시한다.
      - `git push -u <remote_name> <branch_name>`: 원격 브랜치로 최초 푸시

### 18. `git pull`
  - 원격 저장소에서 변경된 내용을 가져와 로컬에 병합한다.
      - `git pull --rebase <remote_name> <branch_name>`: 리베이스를 사용하여 풀

### 19. `git fetch`
  - 원격 저장소의 변경 사항을 로컬로 가져온다.
      - `git fetch <remote_name>`: 원격 저장소의 변경 사항을 가져옴
      - `git fetch --all`: 모든 원격 저장소의 변경 사항을 가져옴
      - `git fetch --prune`: 원격 저장소의 브랜치 정보를 갱신

### 20. `git fetch && git merge`
  - 원격 저장소에서 변경 사항을 가져와 로컬에 병합한다.

>## _태그 관리_

### 21. `git tag`
  - 태그를 생성하고 확인한한다.
      - `git tag -a <tag_name> -m "Tag message"`: 어노테이티드 태그 생성

### 22. `git tag -l`
   - 모든 태그 목록을 확인한다.

### 23. `git tag -d <tag_name>`
  - 태그를 삭제한다.

>## _브랜치 병합_

### 24. `git merge`
  - 두 개의 다른 브랜치를 하나로 합치는 작업을 의미한다.
      - `git merge branch_name`: 현재브랜치에서 대상브랜치를 병합시킴
      - `git merge --squash`: 대상브랜치를 병합할 때, 커밋 이력을 모두 제거하고 작업된 내용만 병합
      - `git merge --no-ff`: fast-forward 방식으로 병합할 때, 병합된 것임을 알리는 커밋 메시지 생성

## _임시 저장 및 복구_

### 25. `git stash`
  - 변경 사항을 임시로 저장하고 나중에 불러올 수 있도록 한다.
      - `git stash list`: 저장한 스태시 목록 확인
      - `git stash apply`: 가장 최근의 스태시를 적용

>## _검색 및 탐색_

### 26. `git grep <search_term>`
   - 소스 코드에서 특정 용어를 검색한한다.

>## _파일 비교_

### 27. `git diff`
   - Working Directory의 변경 사항을 확인한다.
      - `git diff --staged` 또는 `git diff --cached`: Staging Area(인덱스)에 있는 변경 사항을 확인
      - `git diff commit_SHA HEAD`: 특정 커밋과 현재 작업 중인 브랜치 간의 차이 확인
      - `git diff HEAD`: 현재 작업 중인 브랜치의 최신 커밋과 Working Directory 간의 차이를 확인
      - `git diff file1.txt file2.txt`: 파일 간의 변경 사항 확인
      - `git diff --stat branch1..branch2`: 두 브랜치 간의 차이를 확인하고 통계 정보 표시

>## _디버깅 및 히스토리 확인_

### 28. `git bisect`
  - 버그가 처음 발생한 커밋을 찾기 위한 이진 탐색을 수행한다.

### 29. `git show <commit_hash>`
  - 특정 커밋의 변경 내용을 확인한다.

>## _브랜치 조작_

### 30. `git rebase`
   - 브랜치의 기록을 다시 쓰거나 커밋을 합친다.
      - `git rebase -i HEAD~<num>`: 최근 \<num>개의 커밋을 대화형으로 재배치합니다.

>## _정리 및 초기화_

### 31. `git clean -n`
  - 추적되지 않은 파일 및 디렉토리를 확인한다.
