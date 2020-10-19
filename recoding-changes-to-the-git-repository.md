
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

    그리고 git add한 파일을 다시 수정한다면 다음과 같은 status가 나타난다.
    
    $ vim CONTRIBUTING.md
    
    $ git status
    
    On branch master
    
    Your branch is up-to-date with 'origin/master'.

    Changes to be committed:

      (use "git reset HEAD <file>..." to unstage)
    

        new file:   README
    
        modified:   CONTRIBUTING.md

    Changes not staged for commit:

      (use "git add <file>..." to update what will be committed)
    
      (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   CONTRIBUTING.md
    
    If you modify a file after you run git add, you have to run git add again to stage the latest version of the file:
    
### 3. 파일 상태 옵션

    1. short status
    
    $ git status -s
    
     M README
 
    MM Rakefile

    A  lib/git.rb

    M  lib/simplegit.rb

    ?? LICENSE.txt
    
    -> ?? : not tracked, 
    
       A  : added file,
       
       M  : modified file,
       
       MM : modified and staged and modified again,
       
       README : modified but not staged,
       
       lib/simplegit.rb : modified and staged
       
### 4. Ignoring Files

    1. .gitignore
    
    $ cat .gitignore
    
    *.[oa]

    *~
    
    먼저, *.[oa]는 정규표현식을 통해 파일이 .o 또는 .a로 끝나면 그 파일을 track하지 않는다는 뜻이다 
    
    -> The first line tells Git to ignore any files ending in “.o” or “.a” 
    
    두번째로 *~ 는 ~로 끝나는 파일을 무시하겠다는 것이다.
    
    -> The second line tells Git to ignore all files whose names end with a tilde (~), 
    
    which is used by many text editors such as Emacs to mark temporary files. 
      
    he rules for the patterns you can put in the .gitignore file are as follows:

    Blank lines or lines starting with # are ignored. // 빈 줄과 #으로 시작하는 라인은 무시된다 - 주석인듯?

    Standard glob patterns work, and will be applied recursively throughout the entire working tree. - 재귀적으로 모든 패턴에 동작하게 할 수 있다

    You can start patterns with a forward slash (/) to avoid recursivity. // 재귀탐색을 피하기 위해 앞에 '/'을 붙인다

    You can end patterns with a forward slash (/) to specify a directory. // 끝에 '/'를 붙이면 폴더를 명시하는것.

    You can negate a pattern by starting it with an exclamation point (!). // 
    
### 5. git ignore 예시

    # ignore all .a files
    *.a

    # but do track lib.a, even though you're ignoring .a files above
    
    !lib.a

    # only ignore the TODO file in the current directory, not subdir/TODO
    
    /TODO

    # ignore all files in any directory named build
    
    build/

     ignore doc/notes.txt, but not doc/server/arch.txt
     
    doc/*.txt

    # ignore all .pdf files in the doc/ directory and any of its subdirectories
