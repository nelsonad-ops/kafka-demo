<B>Kafka-demo</B><br>
<br>
Kafka cluster creation<br>
kubectl create ns kafka<br>
kubectl apply -f k8s-setup/strimzi-operator.yaml -n kafka<br>
kubectl apply -f k8s-setup/kafka-cluster.yaml -n kafka<br>
kubectl wait kafka/kdemo --for=condition=Ready --timeout=300s -n kafka<br>
<br>
Kafka workload generation<br>
<br>
appendix<br>
[Mac OS Install]<br>
brew install golang<br>
brew install k6<br>
go install go.k6.io/xk6/cmd/xk6@latest<br>
xk6 build --with github.com/mostafa/xk6-kafka@latest<br>
git clone https://github.com/mostafa/xk6-kafka.git<br>
./k6 run --vus 50 --duration 60s xk6-scripts/test_avro_no_schema_registry.js<br>
