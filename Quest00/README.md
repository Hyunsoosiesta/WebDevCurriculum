# Quest 00. 형상관리 시스템

## Introduction
* git은 2021년 현재 개발 생태계에서 가장 각광받고 있는 버전 관리 시스템입니다. 이번 퀘스트를 통해 git의 기초적인 사용법을 알아볼 예정입니다.

## Topics
* git
  * `git clone`, `git add`, `git commit`, `git push`, `git pull`, `git branch`, `git stash` 명령
  * `.git` 폴더
* GitHub

## Resources
* [Resources to learn Git](https://try.github.io)
* [Learn Git Branching](https://learngitbranching.js.org/?locale=ko)
* [Inside Git: .Git directory](https://githowto.com/git_internals_git_directory)

## Checklist
### 1. 형상관리 시스템은 왜 나오게 되었을까요?
여러명이 작업한 코드를 효과적으로 관리하고 합치기 위해.
### 2. git은 어떤 형상관리 시스템이고 어떤 특징을 가지고 있을까요? 분산형 형상관리 시스템이란 무엇일까요?
**분산형 형상관리 시스템**

작업하는 공간, 로컬 스테이징, 원격 스테이징을 분리하여 한 프로젝트에서 독립적인 작업 공간.
<br> eg) 브랜치 / 로컬 스테이지를 가질 수 있음.

### 3. git은 어떻게 개발되게 되었을까요? git이 분산형 시스템을 채택한 이유는 무엇일까요?
[History of Git](https://www.welcometothejungle.com/en/articles/btc-history-git)

### 4. git과 GitHub은 어떻게 다를까요?
- **git**: 소스코드를 관리하는 프로그램
- **GitHub**: git으로 올려놓은 소스코드들이 업로드 되는 공간


### 5.  git의 clone/add/commit/push/pull/branch/stash 명령은 무엇이며 어떨 때 이용하나요? 그리고 어떻게 사용하나요?
- `git clone` 다른 사람의 레포지토리를 내 로컬로 저장함
- `git add` 현재 작업하고 있는 소스코드를 로컬 스테이지에서 깃이 읽을 수 있게 올림
- `git commit` 로컬 스테이지에 올라갈 준비가 된, add된 상태의 소스코드를 로컬스테이지로 올림
- `git push` 로컬 스테이지에 있는 소스코드를 원격 스테이지로 올림
- `git pull` 원격 스테이지에 있는 소스코드를 로컬로 내려받음- `git branch`: 로컬에 브랜치를 생성함
- `git stash` 아직 마무리되지 않은 작업을 잠시 스택에 저장함. 현재 작성한 변경사항을 저장함
- `git stash / git stash save [stash message]` 현재 내용 저장
- `git stash list` list 보기
- `git stash apply` 가장 최근 stash 파일 불러옴
- `git stash [stash name]`  stash name의 stash를 불러옴
- `git stash drop` 가장 최근 stash를 스택에서 지움
- `git stash drop [stash name]` stash name의 stash를 지움
- `git stash apply -p | git apply -R` 적용된 stash를 되돌림
- `git stash show -p [stash name] | git apply -R` 적용된 stash를 되돌림 (특정 stash name 지정)
- `git stash branch [branch name] [stash name]` stash name의 stash로 새로운 브랜치를 만들고 해당 stash는 삭제함

### 6. git의 Object, Commit, Head, Branch, Tag는 어떤 개념일까요? git 시스템은 프로젝트의 히스토리를 어떻게 저장할까요?
[참고 블로그](https://sjh836.tistory.com/37)
- Object: blob, tree, commit, tag가 4대 obj.
  - Blob:  파일 내용. `git add` 시 생성
  - Tree: 파일 디렉. `git commit` 시 생성
- Commit: 작성자, 커밋데이터, 로그 메시지 등 정보가 수정되면 레포에 정보를 저장
- Head: 현재 작업하고 있는 커밋
- Branch: 작업하고 있는 공간
- Tag: 많은 커밋이 쌓이는데, 눈에 띄게 명시하고 싶을 때 태깅을 함. 릴리즈 버전에서 많이 쓰임
  - `git tag` 명령어로 tag들을 조회할 수 있음
  - `git tag <tag name>` **Lightweight tag** - 태그 이름만 남기는 간단한 버전
  - `git tag -a <tag name> -m` **Annotated tag** - 태그에 이름 + 정보를 남김
  - `git tag <new name> <old name>` tag 수정
  - `git tag -d <tag name>` tag 삭제

>**어떻게 프로젝트 히스토리를 저장하는가 ❔**  
blob, tree를 확인하고, status에서 같은 내용이 아닐 시, 새로운 obj를 만들어 저장할 수 있음 그래서 내용이 각기 다른 obj는 다른 tag로 추적할 수 있음

### 7. 리모트 git 저장소에 원하지 않는 파일이 올라갔을 때 이를 되돌리려면 어떻게 해야 할까요?
[참고 블로그 - 카툰](http://www.devpools.kr/2017/01/31/%EA%B0%9C%EB%B0%9C%EB%B0%94%EB%B3%B4%EB%93%A4-1%ED%99%94-git-back-to-the-future/)
- `git reset`: 시간을 되돌림 해당 commit 이후의 로그들 전부 삭제됨. **이미 push한 상태면 local git만 과거로 reset됨**
- `git revert`: 해당 commit만 삭제됨. **push한 상태면 revert 할 수 밖에 없음**

## Quest
* GitHub에 가입한 뒤, [이 커리큘럼의 GitHub 저장소](https://github.com/KnowRe-Dev/WebDevCurriculum)의 우상단의 Fork 버튼을 눌러 자신의 저장소에 복사해 둡니다. ✅
* Windows의 경우 같이 설치된 git shell을, MacOSX의 경우 터미널을 실행시켜 커맨드라인에 들어간 뒤, 명령어를 이용하여 복사한 저장소를 clone합니다. ✅
  * 앞으로의 git 작업은 되도록 커맨드라인을 통해 하는 것을 권장합니다. ✅
* 이 문서가 있는 폴더 바로 밑에 있는 sandbox 폴더에 파일을 추가한 후 커밋해 보기도 하고, 파일을 삭제해 보기도 하고, 수정해 보기도 하면서 각각의 단계에서 커밋했을 때 어떤 것들이 저장되는지를 확인합니다. ✅
* `clone`/`add`/`commit`/`push`/`pull`/`branch`/`stash` 명령을 충분히 익혔다고 생각되면, 자신의 저장소에 이력을 push합니다. ✅

## Advanced
### ➕ Mercurial은 어떤 형상관리 시스템일까요? 어떤 장점이 있을까요?
[Mercurial vs Git - EDUCBA](https://www.educba.com/mercurial-vs-git/)

#### Comparison between Mercurial and Git
|Feature|Mercurial|Git|
|:---:|:---:| :---: |
|Definition|개발자들이 애플리케이션을 관리하는데 사용하는 버전관리 툴.<BR> 비교적 작은 팀에서 프로젝트를 할 때 쓰임.|애플리케이션의 변화를 컨트롤하고 수정하는 버전관리 툴.<br> 소프트웨어 개발 사이클을 유지하는데 사용됨.|
|Developer|Matt Mackall이라는 개발자에 의해 개발되었으며 python과 C언어로 만들어짐.|Linux Torvalds에 의해 개발되었으며 C, Python, Tcl, Shell, Perl로 만들어짐|
|Flexibility in the version history|사용자는 버전 히스토리의 변화에 접근할 수 없으나 이전 커밋을 변화하는 권한이 있음.|사용자는 버전 히스토리를 변화하기 위한 권한이 있으며, 요구사항에 맞게 버전 히스토리를 변경할 수 있음|
|Support for a staging area|스테이징 기능 없음.|스테이징 기능을 제공. 스테이징은 다음에 있을 커밋을 미리 볼 수 있는 장소를 제공함.|
|Branching|브랜칭을 제공함. 그러나 그 구조가 복잡하고 Git과 비교했을 때 강력하지 않음.|강력한 브랜칭 기능을 제공함. 프로젝트마다 쉽게 브랜치를 생성할 수 있음.|
|Ease of use|Git보다 쉽게 사용할 수 있음. 이 툴에 익숙해지면 better experience를 할 수 있음 |Mercurial보다 복잡함. 사용자는 깃을 사용하기 전에 기초적인 개념을 먼저 이해해야함.|
|Target audience|소규모 팀에서 선호함. 경험이 적은 비기너들에게 유용하고 이해하기 쉬움. |대규모 조직에서 선호함. 사용 전에 적절한 hands-on이 필요함.|

### ➕ 실리콘밸리의 테크 대기업들은 어떤 형상관리 시스템을 쓰고 있을까요?
[Why does Facebook take Mercurial over Git ?](https://www.quora.com/Why-did-Facebook-Engineering-team-choose-Mercurial-over-Git-to-meet-their-scalability-challenges)

Facebook : Mercurial 사용 〰 **Save time, Edit fast !**