# ReplicaSet
********************************

## 레플리케이션컨트롤러
1. 레이블 셀렉터
2. 복제본 수
3. 포드 템플릿

### 장점
1. 포드가 없는 경우 새 포드를 항상 실행
2. 노드에 장애가 발생 시 다른 노드에 복제본 생성
3. 수동, 자동으로 수평 스케일링

##### 조회
kubectl get rc

##### 포드를 임의로 정지
kubectl delete pod rc-http-go-znmlz

##### 레플리케이션 정보 확인
kubectl describe rc rc-http-go -> Events 확인

##### 관리 레이블 벗어나기
kubectl get pod -L app  
kubectl label pod rc-http-go-zhdj5 app=http-go2 --overwrite  
kubectl get pod -L app  

##### 레플리케이션컨트롤러 설정 바꾸기
kubectl edit rc rc-http-go

##### 레플리케이션컨트롤러 삭제
kubectl delete rc rc-http-go -> pod 전체 삭제  
--cascade 옵션 사용시 pod 유지됨


********************************