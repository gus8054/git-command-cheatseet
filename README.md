# git-command-cheatseet
자주 사용하는 깃/깃헙 명령어 모음

- `git init` : 저장소 생성

- `git config user.name "[사용자 이름]"` : 사용자 이름 설정
- `git config user.email "[사용자 이메일 주소]"` : 사용자 이메일 주소 설정
- `git config --list` : 설정 확인
- `git config user.name` 또는 `git config --get user.name` : 사용자 이름 확인
- `git config user.email` 또는 git config --get user.email` : 사용자 이메일 주소 확인
- `git config --unset user.name` : 사용자 이름 삭제
- `git config --unset user.email` : 사용자 이메일 주소 삭제
- `git config --global user.name "[사용자 이름]"` : 글로벌 사용자 이름 설정
- `git config --global user.email "[사용자 이메일 주소]"` : 글로벌 사용자 이메일 주소 설정

>Git config 우선순위
>1. 로컬 : Repository/.git/config
>
>3. 글로벌 : C:/Users/사용자_계정/.gitconfig
>4. 시스템 : C:/Program Files/Git/etc/gitconfig

- `git help` : 도움말

- `git status` : 저장소의 상태 정보
- `git status --short` : 저장소의 상태 요약 정보

>상태 문자는 앞문자 + 뒤문자로 구성됨.</br>
>Untracked 파일은 예외적으로 `??` 로 표시됨. 아래의 상태문자는 모두 Tracked 파일이라 가정함.
>- 앞 문자 : Staging Area와 Repository의 관계
>  
>   * `A` : Repository에 없던 파일이 Staging Area에 있음
>  
>   * `M` : Repository에 있는 파일이 Staging Area에 수정되어 있음
>   * `D` : Repository에 있는 파일이 Staging Area에 삭제되어 있음 (Staging Area에 해당 파일이 없는 것과 해당 파일의 삭제내역이 Staging Area에 있는 것은 서로 다른 의미이니 주의)
>- 뒤 문자 : 앞 문자가 존재하면 Working Directory와 Staging Area관계. 앞 문자가 공백이면 Working Directory와 Repository의 관계
>   * `M` : Staging Area 또는 Repository 의 파일이 Working Directory에서 수정되어 있음
>  
>   * `D` : Staging Area 또는 Repository 의 파일이 Working Directory에서 삭제되어 있음

- `git add [파일 이름]` : 해당 파일을 Staging Area로 이동.
  
- `git add [디렉터리 이름]` : 해당 디렉터리 내의 모든 파일들을 Staging Area로 이동
- `git add .` : Working Directory안의 모든 파일들을 Staging Area로 이동
- `git commit` : Staging Area의 모든 파일들을 Repository로 이동, VI 에디터가 실행되며 메시지를 작성
- `git commit -m "[메시지]"`: Staging Area의 모든 파일들을 Repository로 이동, 메시지까지 한 번에 작성
- `git commit -am "[메시지]"` : Working Directory의 모든 파일들을 Staging Area를 거치지 않고 Repository로 이동, 메시지까지 한 번에 작성
- `git log` : 커밋 히스토리를 출력
- `git log -[정수]` : 커밋 히스토리를 최근 순으로 정수개 출력
- `git log --patch` : 각 로그의 상세내역을 최근 순으로 출력
- `git log --pretty=oneline` : 커밋별로 로그가 한 줄로 정리되어 출력
- `git log --oneline` : `git log --pretty=oneline` 와 커밋해시을 제외하고 동일. 커밋해시가 앞에서 부터 7번째까지만 출력됨.
- `git log --graph` : 각 커밋 로그를 그래프 형태로 출력
- `git log --all` : 모든 브랜치에 대해 커밋 로그를 출력 ( 원래는 현재 브랜치에 대한 로그만 출력됨 )
- `git show` : 최근 커밋의 상세정보를 출력 ( = `git log --patch -1` )
- `git show [커밋 해시]` : 해당 커밋의 상세 정보 출력
- `git show [커밋 해시]:[파일 이름]` : 해당 커밋에서의 해당 파일을 출력 ( 원래는 + 또는 -로 변경사항까지 출력됨 )

>커밋 참조 개체의 상대위치 표시
>- `^` : 바로 이전
>  
>- `~[정수]` : 정수개 이전
>- 예: `HEAD^` = `HEAD~1` = HEAD개체의 바로 이전 커밋
>- 예: `master^^` = `master~2` = master개체의 앞의 앞 커밋

- `git diff` : 최근 커밋과 Unstaged 파일들을 비교
  
- `git diff --staged` : 최근 커밋과 staged 파일들을 비교
- `git diff [커밋 해시1] [커밋 해시2]`: 두 커밋 사이의 파일들을 비교. 커밋 해시2와 비교해서 커밋 해시1에서 추가된 부분은 +로, 삭제된 부분은 -로 표시
- `git reset` : Staging Area의 전체 내역을 삭제. Working Directory 내용은 변경되지 않는다는 점에 주의.
- `git reset [파일 이름]` : Staging Area의 해당 파일의 내역을 삭제.
- `git reset [경로]` : Staging Area의 해당 경로내의 파일들의 내역을 삭제.
- `git reset [커밋 해시]` : 해당 커밋으로 현재 브랜치 참조를 변경
- `git reset --hard [커밋 해시]` : 해당 커밋으로 현재 브랜치 참조를 변경 ( Working Directory 복구, Staging Area 복구, Commit 복구)
- `git reset --mixed [커밋 해시]` : 해당 커밋으로 현재 브랜치 참조를 변경 ( Staging Area 복구, Commit 복구) -> 기본값
- `git reset --soft [커밋 해시]` : 해당 커밋으로 현재 브랜치 참조를 변경 ( Commit 복구)
- `git commit --amend` 최근 커밋을 수정, 최근 커밋과 스테이징 내용을 병합하는 방식. VI 에디터가 열리며 커밋 메시지도 수정 가능함.
- `git commit --amend -m "[메시지]"`: 최근 커밋을 수정, 최근 커밋과 스테이징 내용을 병합하는 방식. 커밋 메시지도 같이 수정.
- `git checkout [파일 이름]` : 해당 파일이 Modified 상태면 Unmodified 였던 상태로 복구.
- `git checkout .` : Modified 상태인 모든 파일을 Unmodified 였던 상태로 복구
- `git checkout [커밋 해시]` : 해당 커밋으로 HEAD 참조 변경
- `git reflog` : HEAD가 참조한 커밋 이력들을 최신 순으로 출력
- `git remote` : 현재 브랜치에 추가된 원격 저장소 리스트 출력
- `git remote --verbose` : 현재 브랜치에 추가된 원격 저장소 리스트를의 fetch주소 및 push주소 출력
- `git remote add [원격 저장소의 이름] [원격 저상소 url]` : 원격 저장소 추가
- `git remote rm [원격 저장소 이름]` : 해당 원격 저장소와의 연결 설정 삭제
- `git remote show [원격 저장소 이름]` : 해당 원격 저장소의 상세정보 출력
- `git push --set-upstream-to [원격 저장소 이름] [로컬 저장소 브랜치 이름] : 원격 저장소와 로컬 저장소의 브랜치간의 업스트림을 설정하고 원격 저장소에 push
- `git push` : 업스트림 설정이 되어있다면 원격 저장소에 push
- `git pull` : 업스트림 설정이 되어있다면 원격 저장소에 pull
