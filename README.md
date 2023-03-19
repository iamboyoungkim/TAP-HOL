# TAP-HOL
Tanzu Application Platform Hands-On-Labs 페이지 입니다.

## 설치 제품
본 가이드에서 다루는 Tanzu 설치 솔루션 및 버전은 다음과 같습니다.
|제품명|Version|
|---|---|
|TAP|1.4.1|

* TAP설치를 위해서는 아래와 같은 Kubernetes Cluster가 필요합니다. 이 Lab에서는 TKG를 이용해서 진행합니다.
  - Kubernetes v1.23 ~ v1.25
  - AKS / EKS / GKE / Minikube / TKGm / TKGs (vSphere with Tanzu v7.0 U3a)

## 1. TAP 환경 확인 및 구성
- [설치 환경 확인](./install/check.md)
- [개발자용 네임스페이스 설정](./install/dev-namespace.md)

## 2. 애플리케이션 배포 및 등록
간단한 Spring Boot 애플리케이션을 TAP에 배포합니다.
- [애플리케이션 배포](./tap/app-deploy.md)
- [catalog 등록](./tap/catalog.md)

## 3. App Live View
배포한 applications의 Live View를 확인합니다.
- [App Live View](./tap/app-live-view.md)

## 4. GUI 둘러보기
TAP GUI를 둘러보며 기능을 알아봅니다.
- [TAP GUI](./tap/gui.md)

## 5. TAP Supply Chain 구성
OOTB Basic Supply Chain을 Testing and Scanning으로 변경합니다.    
구성 정보를 자동적으로 git repository에 push하도록 gitops 환경을 구성합니다.
- [Supply Chain - Testing and Scanning](./tap/ootb-testing-and-scanning.md)
- [GitOps](./tap/gitops.md)

## 6. 개발 환경 개선을 위한 IDE 경험
- [동적 배포와 원격 디버깅](./tap/hotdeploy_debug.md)

## 7. Acclerator 커스터마이징 (TBU)


