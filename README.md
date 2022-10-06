## GIT 연습을 위해 생성된 프로젝트입니다.

### 최초 세팅
1. git init : 현재 폴더에 git을 사용할 수 있도록 세팅   
2. git branch -M main : 메인 브랜치 이름을 main 으로 변경 (이건 경우에 따라 필요 없을수도 있음)   
3. git remote add origin 원격주소 : 원격주소 정보를 추가하며 원격주소 별명을 origin으로 설정함.   
   
---   
   
### 커밋(commit)
1. git add   
1-1. git add 파일명 : 수정한 파일 중 파일명 하나만 커밋 대기장소(staging area)에 올림   
1-2. git add . : 수정된 파일들 전부 커밋 대기장소(staging area)에 올림   
2. git commit -m "커밋 메세지" : 커밋에 대한 메세지 작성 (내용은 직관적으로 적을수록 좋음)   
3. git push -u 원격주소 main : 원격주소에 있는 main 브랜치에 커밋 내용 push   

---

### 상태창(status)

#### 상태 확인하기
1. git status : 현재 브랜치 위치 및 변경된 파일이 있는지 보여줌   
   
#### 커밋내역 확인하기
1. git log --graph --oneline --all : 커밋 내역을 그래프로 보여줌    
   
---
   
### 브랜치(branch)
   
#### 브랜치 생성 및 이동
1. git branch 브랜치명   
2. git switch 브랜치명   
   
#### 브랜치 삭제(delete)하기
1-1. git branch -d 브랜치명 : 병합이 완료된 브랜치 삭제   
1-2. git branch -D 브랜치명 : 병합하지 않은 브랜치 삭제   
   
---

### 원격브랜치(remote branch)
   
#### 원격서버로부터 파일 로컬 저장소에 내려받기
1. git clone 원격저장소주소   
   
#### 원격서버로부터 파일 최신화 (push 충돌날 경우)
1. git pull origin 브랜치명   
   
---
   
### 병합(merge)
   
#### 메인 브랜치에 작업 브랜치 병합(merge)하기 (일반적인 3-way merge)   
1. git branch 메인 브랜치   
2. git merge 작업 브랜치   
   
#### 베이스 재설정(rebase)후 병합(merge)하기 (강제 fast-forward merge, 위험도 ★★★★★)
1. git switch 작업 브랜치 : 작업 브랜치로 이동   
2. git rebase 메인 브랜치 : 작업 브랜치를 메인 브랜치 끝으로 이동시킴   
3. git switch 메인 브랜치 : 메인 브랜치로 다시이동   
4. git merge 작업 브랜치 : 메인 브랜치와 작업 브랜치를 병합   
   
#### 스콰시(squash)후 병합(merge)하기 (커밋 똑 떼서 붙여넣기)
1. git switch 메인 브랜치 : 메인 브랜치로 이동   
2. git merge --squash 작업 브랜치 : 메인 브랜치에 작업 브랜치를 스콰시 시키기   
3. git commit -m '메세지' : 커밋 메세지 작성   
   
---

### 되돌리기(restore, revert, reset)
   
#### 파일 하나를 이전 커밋 상태로 복구   
1. git restore 파일명   

#### 파일 하나를 특정 커밋 시점으로 복구   
1. git restore --source 커밋아이디 파일명   
   
#### 스테이징 취소
1. git restore --staged 파일명   
   
#### 과거의 특정 커밋내역 취소
1. git revert 커밋아이디   
   
#### 해당 커밋 생성 시점으로 파일 되돌리기 (git add 안해놓은 파일들은 유지됨)
1. git reset 커밋아이디   
1-1. git reset --hard 커밋아이디 : 커밋아이디 시점의 파일을 완전 삭제합니다.   
1-2. git reset --soft 커밋아이디 : 커밋아이디 시점의 파일이 staging area에 남아있습니다. git commit 가능   
1-3. git reset --mixed 커밋아이디 (기본) : 커밋아이디 시점의 파일이 staging 전 상태가 됩니다. git add 및 commit 가능   
   
---
   
### 임시저장(stash)
   
#### 작업내역을 임시저장   
1. git stash   

#### 작업내역을 메모와 함께 임시저장
1. git stash save "메모"   
   
#### 임시저장 리스트 보기
1. git stash list   
   
#### 보관했던 코드 다시 불러오기 (가장 최근에 저장한 코드)
1. git stash pop   
   
### 특정 stash 삭제
1. git stash drop 삭제할id   
   
### 모든 stash 삭제
1. git stash clear   
   
### 일부 코드만 stash 하고 싶을때
1. git stash -p   
   
