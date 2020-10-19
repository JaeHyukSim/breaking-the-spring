
## 1. 깃 리포지토리에 변화를 기록하기

    파일의 상태는 크게 두가지로 구분된다.

    - tracked or untracked - 
    
    tracked 파일은 3가지 상태로 표시된다
    
    - modified or unmodified or staged - 
    
    
![the-life-cycle-of-the-status](https://user-images.githubusercontent.com/55395239/96400361-7877f600-120b-11eb-93b7-cb70a2a94164.PNG)

### 2. 파일 상태 확인하기

    $ git status
    
    Your branch is up-to-date with 'origin/master'.
    
    nothing to commit, working directory clean
    
    깃의 상태는 tracked된 파일들이 수정되지 않았거나 untracked files를 찾을 수 없으면 up-to-date라 표기된다
    
    none of your tracked files are modified. Git also doesn’t see any untracked files, or they would be listed here.
    
    그렇다면, 이번엔 새로운 README 파일을 만들어서 변화를 줘 보자.
    
    Let’s say you add a new file to your project, a simple README file. 
    
    만약 README파일이 없었는데 추가됐다면 git status 명령어를 입력하면 다음과 같은 모습을 볼 수 있다.
    
    If the file didn’t exist before, and you run git status, you see your untracked file like so:
    
    $ echo 'My Project' > README
    
    $ git status
    
    On branch master

    Your branch is up-to-date with 'origin/master'.

    Untracked files:

      (use "git add <file>..." to include in what will be committed)

        README

    nothing added to commit but untracked files present (use "git add" to track)
    
    즉, 'untracked'된 파일 하나를 인식한다.
    
    따라서 untracked 파일이란 다음과 같이 정의할 수 있다
    
    -> 이전 스냅샷에서 볼 수 없었던 새로운 파일이 추가된 것!
    
    Untracked basically means that Git sees a file you didn’t have in the previous snapshot (commit)
    
    그렇다면, 이것을 untracked 파일에서 -> tracked 파일로 바꾸려면 어떻게 해야 할까?
    
    $ git add README
    
    이 명령어를 통해 tracked 파일로 바꿀 수 있다!!
    
    $ git status를 보면
    
    $ git status
    
    On branch master
    
    Your branch is up-to-date with 'origin/master'.
    
    Changes to be committed: // 'You can tell that it’s staged'
    
      (use "git restore --staged <file>..." to unstage) // 다시 untracked로 바꾸고 싶다면 사용하는 명령어로 해석할 수 있다.

    new file:   README
    
    git add를 file 또는 directory에 수행할 수 있는데, 만약 directory에 수행했다면, 재귀적으로 내부 모든 디렉토리 및 파일을 add한다
    
    The git add command takes a path name for either a file or a directory; if it’s a directory, the command adds all the files in that directory recursively.
