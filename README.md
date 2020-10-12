# Git-Issue
내가 겪은 깃 이슈들 정리

### main branch의 README.md파일과 master branch의 파일을 합치고 싶을 때(두 개의 브랜치, 다른 커밋 히스토리)
1. git fetch --all : main branch 추적 위해.
  - 현재 시점에서 진짜 최신 데이터로 추적 상황을 알아보려면 먼저 서버로부터 최신 데이터를 받아온 후에 추적 상황을 확인해야 한다. 
  - git fetch 명령을 실행하면 서버에는 존재하지만, 로컬에는 아직 없는 데이터를 받아와서 저장한다. 이 때 워킹 디렉토리의 파일 내용은 변경되지 않고 그대로 남는다. 서버로부터 데이터를 가져와서 저장해두고 사용자가 Merge 하도록 준비만 해둔다. 
  - 설명 출처: <https://git-scm.com/book/ko/v2/Git-%EB%B8%8C%EB%9E%9C%EC%B9%98-%EB%A6%AC%EB%AA%A8%ED%8A%B8-%EB%B8%8C%EB%9E%9C%EC%B9%98>
    ![1](https://user-images.githubusercontent.com/66557175/95723726-6b5d8300-0cb0-11eb-8e98-a34b3c1e75ad.png)
    
2. git pull --rebase origin main : main branch 변경사항을 master에 적용
  - rebase 명령으로 한 브랜치에서 변경된 사항을 다른 브랜치에 적용할 수 있다.
  - Rebase는 보통 리모트 브랜치에 커밋을 깔끔하게 적용하고 싶을 때 사용한다. Rebase 한 브랜치의 Log를 살펴보면 히스토리가 선형이다.
  - 설명 출처: <https://git-scm.com/book/ko/v2/Git-%EB%B8%8C%EB%9E%9C%EC%B9%98-Rebase-%ED%95%98%EA%B8%B0>
    ![2](https://user-images.githubusercontent.com/66557175/95734986-2f7dea00-0cbf-11eb-9210-6b2d02957201.png)
  
3. git checkout main
  - main branch로 변경
    ![3](https://user-images.githubusercontent.com/66557175/95734990-31e04400-0cbf-11eb-90d8-66d60c3fe6a8.png)
  
4. git merge master
  - master branch를 합침
    ![4](https://user-images.githubusercontent.com/66557175/95734998-34429e00-0cbf-11eb-9769-8096bc28d97f.png)
  
5. git push origin main 
  - 서버로 전송
    ![5](https://user-images.githubusercontent.com/66557175/95735002-360c6180-0cbf-11eb-839b-496a4aad4dd5.png)
    
 **참고 사항:** 이미 공개 저장소에 Push 한 커밋을 Rebase 하지 마라. 로컬 브랜치에서 작업할 때는 히스토리를 정리하기 위해서 Rebase 할 수도 있지만, 리모트 등 어딘가에 Push로 내보낸 커밋에 대해서는 절대 Rebase 하지 말아야 한다. <br>
  출처: <https://git-scm.com/book/ko/v2/Git-%EB%B8%8C%EB%9E%9C%EC%B9%98-Rebase-%ED%95%98%EA%B8%B0>

