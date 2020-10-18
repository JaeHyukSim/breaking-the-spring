
# 깃 리포지토리 생성하기

### 깃 리포지토리를 생성하는 방법은 2가지가 있습니다.

    1. 아직 버전 컨트롤되지 않은 local directory를 Git repository로 바꾸기
    
    2. 깃 리포지토리에 존재하는 파일을 로컬로 가져오기
    
### 1. 이미 로컬에 있는 폴더를 리포지토리로 초기화하기

    1. git init
        
        git init을 통해 .git 폴더에 깃 리포지토리에 필요한 구성요소들을 얻을 수 있습니다! 
        
        (내부적으로 어떻게 수행되는지는 나중에 공부하기! - 10.1 Plumbing and Porcelain)
        
        This creates a new subdirectory named .git that contains all of your necessary repository files — a Git repository skeleton. 
        
    2. git add
    
        먼저 파일을 추적할 수 있도록 합니다.
        
        you should probably begin tracking those files...
        
    3. git commit
    
        initial commit을 수행합니다.
        
        and do an initial commit.
        
-----------
    
You typically obtain a Git repository in one of two ways:

You can take a local directory that is currently not under version control, and turn it into a Git repository, or

You can clone an existing Git repository from elsewhere.

In either case, you end up with a Git repository on your local machine, ready for work.

If you want to start version-controlling existing files (as opposed to an empty directory), 

you should probably begin tracking those files and do an initial commit. 

You can accomplish that with a few git add commands that specify the files you want to track, 

followed by a git commit:

$ git add *.c

$ git add LICENSE

$ git commit -m 'Initial project version'

We’ll go over what these commands do in just a minute. At this point, you have a Git repository with tracked files and an initial commit.


-------------
