1.  安裝 Redhat Openshift Red Hat Integration - AMQ Streams(OperatorHub)
2. 建立kafka cluster
```
oc apply -f ./yaml/kafka-cluster.yaml -n kafka-demo
```

3. 建立transaction-records Topic
```
oc apply -f ./yaml/transaction-records-tpoic.yaml -n kafka-demo
```

4. 查看已建立的資源
```
oc project kafka-demo
oc get kafka  -n kafka-demo
oc get kafkatopic  -n kafka-demo
```

6. 開啟兩個視窗分別啟動create_consumer.sh及create_producer.sh腳本
```
./scripts/create_consumer.sh
./scripts/create_producer.sh
```
7. 在producer輸入值隨後在comsumer也收到了值

8. 關閉所有腳本在建立一個comsumer讀取 transaction-records Topic
```
oc exec -it my-cluster-kafka-0 -- bin/kafka-console-consumer.sh --from-beginning --bootstrap-server my-cluster-kafka-brokers:9092 --topic transaction-records
```
