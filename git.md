# GIT 


### 1. Version Control System (VCS)란?

    * 참고 : Git - document - book

    프로젝트 개발을 하면서 파일 또는 파일들의 변화가 계속 이루어집니다.
    
    그러다가 이전 버전으로 되돌아가고 싶을 때가 있습니다.
    
    이때 사용할 수 있는 것이 Version Control System입니다. 
    
    (Using a VCS generally means that if you screw things up or lose files, you can easily recover.)
    
    Version Control이란 파일 또는 파일들의 변화들을 기록하여 이전 버전으로 
    
    돌아가고 싶을 때 그것을 가능하게 해주는 system 입니다. 
    
    Version control is a system that records changes to a file or set of files over time so that you can recall specific versions later. 

### 2. Distributed Version Control Systems (DVCS (such as Git, Mercurial, Bazaar or Darcs))

    GIT은 서버가 다운되어도 모든 파일을 복구할 수 있습니다.
    
    - 깃허브에 연결된 모든 사용자들은 단순히 최신 파일을 가지고 있는 것이 아니라, 변화된 모든 과정을
    
    로컬에 저장했습니다.
    
    따라서 서버가 다운되어도 그 어떤 사용자의 리포지토리로부터 모든 프로젝트를 복구할 수 있습니다.
    
    clients don’t just check out the latest snapshot of the files; rather, they fully mirror the repository, 
    including its full history. Thus, if any server dies, and these systems were collaborating via that server, 
    any of the client repositories can be copied back up to the server to restore it. 
    Every clone is really a full backup of all the data.
    
![getting-started-DVCS](https://user-images.githubusercontent.com/55395239/96369603-01ece100-1196-11eb-87ed-439595f1c91d.JPG)
