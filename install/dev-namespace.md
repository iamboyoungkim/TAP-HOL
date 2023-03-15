# 워크로드 배포를 위한 개발자용 네임스페이스 구성

본 가이드는 TAP에서 워크로드 배포를 위한 개발자용 네임스페이스를 구성하는 방법에 대해 설명합니다. 워크로드를 생성하려면 네임스페이스에 권한이 필요하며, 다음과 같이 두 가지 방법을 지원합니다.
- 단일 사용자 액세스 활성화
- 쿠버네티스 RBAC을 사용하여 추가 사용자 액세스 활성화

본 가이드에서는 단일 사용자 액세스 활성화 방법에 대해서만 설명하며, 쿠버네티스 RBAC을 사용한 추가 사용자 엑세스 활성화 방법에 대해서는 [네임스페이스 구성 방법에 대한 링크](https://docs.vmware.com/en/VMware-Tanzu-Application-Platform/1.4/tap/namespace-provisioner-legacy-manual-namespace-setup.html)를 참고하시기 바랍니다.

본 가이드에서는 개발자용 네임스페이스로 default 네임스페이스를 사용합니다.


## 1. 환경변수 설정
|변수명|설명|
|------|---|
|REGISTRY_SERVER|사설 레지스트리 접속 FQDN
|REGISTRY_USERNAME|사설 레지스트리 접속 ID
|REGISTRY_PASSWORD|사설 레지스트리 접속 비밀번호
|YOUR_NAMESPACE|워크로드를 배포할 네임스페이스 명

~~~
export REGISTRY_SERVER=private-harbor.tanzu.lab
export REGISTRY_USERNAME=admin
export REGISTRY_PASSWORD=VMware1!
~~~

## 2. 레지스트리 크리덴셜 추가
이미지 레지스트리 크리덴셜을 다음과 같이 추가합니다.
```
tanzu secret registry add registry-credentials --server REGISTRY_SERVER --username REGISTRY_USERNAME --password REGISTRY_PASSWORD --namespace default
```

만일 에러가 발생하면, 다음과 같이 kubectl 명령어를 이용하여 크리덴셜을 추가해도 됩니다.
```
kubectl create secret docker-registry registry-credentials --docker-server=REGISTRY_SERVER --docker-username=REGISTRY_USERNAME --docker-password=REGISTRY_PASSWORD -n default
```

## 3. 네임스페이스에 권한 부여
다음 코드를 실행하여 시크릿, 공급망을 실행할 서비스 계정, 개발자 네임스페이스에 서비스 계정을 승인하는 RBAC 규칙을 추가합니다.
~~~
cat <<EOF | kubectl -n default apply -f -
apiVersion: v1
kind: Secret
metadata:
  name: tap-registry
  annotations:
    secretgen.carvel.dev/image-pull-secret: ""
type: kubernetes.io/dockerconfigjson
data:
  .dockerconfigjson: e30K
---
apiVersion: v1
kind: ServiceAccount
metadata:
  name: default
secrets:
  - name: registry-credentials
imagePullSecrets:
  - name: registry-credentials
  - name: tap-registry
---
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: default-permit-deliverable
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: deliverable
subjects:
  - kind: ServiceAccount
    name: default
---
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: default-permit-workload
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: workload
subjects:
  - kind: ServiceAccount
    name: default
EOF
~~~

본 단계를 성공적으로 마치셨습니다.