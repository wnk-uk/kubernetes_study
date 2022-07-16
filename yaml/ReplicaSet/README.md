# ReplicaSet
********************************

## 1. 레플리케이션컨트롤러
1. 레이블 셀렉터
2. 복제본 수
3. 포드 템플릿

### 장점
1. 포드가 없는 경우 새 포드를 항상 실행
2. 노드에 장애가 발생 시 다른 노드에 복제본 생성
3. 수동, 자동으로 수평 스케일링

##### <span style="color:yellow">조회</span>
kubectl get rc

##### <span style="color:yellow">포드를 임의로 정지</span>
kubectl delete pod rc-http-go-znmlz

##### <span style="color:yellow">레플리케이션 정보 확인</span>
kubectl describe rc rc-http-go -> Events 확인

##### <span style="color:yellow">관리 레이블 벗어나기</span>
kubectl get pod -L app  
kubectl label pod rc-http-go-zhdj5 app=http-go2 --overwrite  
kubectl get pod -L app  

##### <span style="color:yellow">레플리케이션컨트롤러 설정 바꾸기</span>
kubectl edit rc rc-http-go

##### <span style="color:yellow">레플리케이션컨트롤러 삭제</span>
kubectl delete rc rc-http-go -> pod 전체 삭제  
--cascade 옵션 사용시 pod 유지됨

##### <span style="color:yellow">  레플리케이션컨트롤러 스케일링 방법 </span>  
kubectl apply -f http-go-rc-v2.yaml  
kubectl edit rc http-go  -> editor  
kubectl scale rc http-go --replicas=5   -> cli



## 2. 레플리카셋
### 레플리케이션컨트롤러 vs 레플리카셋
1. 기능은 거의 동일하게 동작
2. 레플리카셋이 더 풍부한 표현식 포드 셀렉터 사용 가능  
- 레플리케이션컨트롤러: 특정 레이블을 포함하는 포드가 일치하는지 확인  
- 레플리카셋: 특정 레이블이 없거나 해당 값과 관계없이 특정 레이블 키를 포함하는 포드를 매치하는지 확인  

##### <span style="color:yellow">조회</span>
kubectl get rs
kubectl describe rs http-go-rs
kubectl delete rs http-go-rs

********************************