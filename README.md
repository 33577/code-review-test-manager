# 코드 리뷰 테스트 매니저

## Creator

### 설명 
creator는 여러 개의 코드 리뷰 테스트용 리포지토리를 자동으로 생성하기 위한 스크립트입니다. \
아래 명령어는 code-review-test-1부터 code-review-test-100까지의 리포지토리와 PR을 생성합니다.
```bash
code-review-test $ ./code-review-test-manager/creator 1 100
```

생성된 리포지토리 하나는 한 명의 지원자에게 할당됩니다. 지원자는 리포지토리에 있는 하나의 PR을 리뷰하게 됩니다.

### Requirements
- Git
- [Github CLI](https://cli.github.com/)

### 사용 방법

1. 로컬 환경에 코드 리뷰 테스트용 디렉터리를 만든다. 

    ```bash
    $ mkdir code-review-test
    $ cd code-review-test
    ```

2. 이미 만들어둔 코드 리뷰 테스트 프로젝트 리포지토리가 있다면 클론하고, 없다면 새로 만든다.

    - 클론
      - PR을 위한 브랜치까지 Pull 받아야 한다.
        ```bash
        code-review-test $ git@github.com:$ORG_NAME/original-code-review-test.git
        code-review-test $ git@github.com:33577/code-review-test-manager.git
        
        code-review-test $ cd original-code-review-test
        code-review-test/original-code-review-test $ git pull origin add-reservation-service:add-reservation-service
        code-review-test/original-code-review-test $ cd ..
        ```
    - 아래와 같은 디렉터리 구조여야 한다.
       ``` 
        - code-review-test
            - original-code-review-test
            - code-review-test-manager # This Repository
       ```

3. gh (github cli)를 설치하고 로그인한다.

    ```bash
    code-review-test $ brew install gh 
    code-review-test $ gh auth login
    ```

4. creator의 ORG_NAME을 설정한다.
   
5. creator를 실행한다. 
   - 아래 명령어는 code-review-test-1부터 code-review-test-100까지의 리포지토리와 PR을 생성한다.
    
    ```bash
    code-review-test $ ./code-review-test-manager/creator 1 100
    ```

6. 생성된 리포지토리에 지원자를 Collaborator로 초대한다. 
   - [[Github Docs] 조직의 리포지토리에 외부 협력자 추가
](https://docs.github.com/ko/enterprise-cloud@latest/organizations/managing-user-access-to-your-organizations-repositories/adding-outside-collaborators-to-repositories-in-your-organization)
