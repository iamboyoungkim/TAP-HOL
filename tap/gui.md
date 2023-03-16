## Tanzu Application Paltform GUI 알아보기
이번 실습에서는 Spring Boot 앱에서 개발자들에게 제공되는 Actuator를 기반으로 한 정보들을 TAP에서 효과적으로 보여줄 수 있는 방법과 
그리고 TAP GUI 화면들에서 대해서 알아보겠습니다.


### 1. TAP GUI 메뉴 둘러보기
TAP GUI의 메뉴들을 살펴보도록 하겠습니다.

#### Catalog
앞 세션에서 App를 배포하고 해당 App들이 등록된 화면입니다.

Catalog 목록중 "tanzu-java-web-app"을 클릭 해보겠습니다.
![](../images/gui-01-01.png)

SYSTEM의 "tanzu-roadshow"을 클릭 해보겠습니다.
![](../images/gui-01-02.png)


오른쪽에 Has components목록과 APIs 목록을 확인 할 수 있습니다.
![](../images/gui-01-03.png)


"Diagram" 클릭하겠습니다.
![](../images/gui-01-04.png)


"Diagram" 확인 할 수 있습니다.
![](../images/gui-01-05.png)



#### Documentation
배포한 APP들의 상세한 설명을 볼 수 있는 메뉴입니다.
![](../images/gui-02.png)



#### Accelerators
APP들을  Accelerators에 등록할수 있으며, 현재 등록된 App들을 보여주는 메뉴입니다. 
![](../images/gui-03.png)



#### APIs
API 목록을 확인 할 수 있는 메뉴입니다.
"tanzu-java-web-app-api" 클릭합니다.
![](../images/gui-04.png)


"Definition"을 클릭합니다.
![](../images/gui-05.png)


API 목록을 확인 할 수 있습니다.
![](../images/gui-06.png)

#### WORKLOADS
배포된 Workload 목록을 확인 할 수 있는 메뉴입니다.
"tanzu-java-web-app" 을 클릭합니다.
![](../images/gui-07.png)


tanzu-java-web-app의 파이프라인  정보 및 단계별 상황을 확인 할 수 있습니다. 
![](../images/gui-08.png)



