## Git

### Characteristics of Git

-   단순한 구조와 빠른 속도
-   분산형 저장소 지원
-   비선형적 개발(수천개의 브랜치) 가능
-   오프라인 작업 가능
-   GitHub, GitLab, Bitbucket 같은 클라우드 기반 협업 플랫폼 지원

![](https://docs.getdbt.com/img/docs/dbt-cloud/cloud-ide/git-overview.png)

  
source: [https://docs.getdbt.com/docs/collaborate/git-version-control"](https://docs.getdbt.com/docs/collaborate/git-version-control")

### Pros of Git

-   소스코드 주고받지 않고도 동시 작업 가능
-   수정 내용은 commit 단위로 관리하여 배포는 물론 원하는 시점으로 Checkout 가능
-   새로운 기능 개발을 Branch로 관리하여 성공적으로 개발이 완료되면 Main Branch에 Merge하여 반영
-   인터넷이 연결 없이도 개발 가능

### Git Workflow

![](https://cloudstudio.com.au/wp-content/uploads/2021/06/GitWorkflow-4.png)

  
source: [https://cloudstudio.com.au/2021/06/26/git-command/"](https://cloudstudio.com.au/2021/06/26/git-command/")

#### **Local**

##### 1\. Working Directory

-   파일을 수정하거나 작업하는 영역
-   수정된 파일을 Untracked(추적되지 않음) 상태
-   수정 후, 파일을 Staging Area로 올리기 위해 `git add` 명령어 사용

##### 2\. Staging Area

-   커밋 준비가 된 파일들이 올라가는 공간
-   `git add`를 통해 특정 파일이나 모든 파일을 스테이징할 수 있음
-   이후 `git commit` 명령으로 파일을 Local Repository로 저장

##### 3\. Local Repository

-   로컬에서 관리되는 Git 저장소
-   `git commit`으로 파일의 변경 사항을 여기에 저장하며 commit 히스토리가 축적됨
-   원격 저장소로 변경 사항을 업로드하려면 `git push`를 사용

#### **Remote**

##### 4\. Remote Repository

-   GitHub, GitLab 같은 서버에 있는 저장소
-   협업을 위해 여러 개발자들이 접근 가능
-   로컬에서 원격 저장소로 데이터를 보내기 위해 `git push`를 함
-   원격 저장소에서 데이터를 가져오기 위해 `git pull`이나 `git fetch` 사용

### _System is not Service_

-   Git은 System으로 버전 관리를 위한 도구

-   Remote Repository는 Service로 Git의 데이터를 저장하고 협업 및 관리 기능을 제공
