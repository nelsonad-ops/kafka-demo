# kafka-demo



Kafka cluster creation
kubectl create ns kafka
kubectl apply -f k8s-setup/strimzi-operator -n kafka
kubectl apply -f k8s-setup/kafka-cluster -n kafka
kubectl wait kafka/kdemo --for=condition=Ready --timeout=300s -n kafka

Kafka workload generation


appendix
[Mac OS Install]
brew install golang
brew install k6
go install go.k6.io/xk6/cmd/xk6@latest
xk6 build --with github.com/mostafa/xk6-kafka@latest
git clone https://github.com/mostafa/xk6-kafka.git
./k6 run --vus 50 --duration 60s xk6-kafka/scripts/test_json.js