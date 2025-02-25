# full-stack-docker-compose

This project contains a unified docker-compose for starting a full stack chain (a blockchain, an API, an explorer, a wallet) 
for local testing. 

## Chain simulator

Directory `chain-simulator` contains a `docker-compose.yaml` that includes the following services:
- a chain simulator
- an Elasticsearch cluster that will contain outport data from the chain
- an Events notifier client that will publish all the events via a RabbitMQ queue
- an API instance with all its dependencies (Redis, RabbitMQ, and so on)
- an instance of Explorer
- an instance of Lite Wallet

### How to start

```shell
cd chain-simulator
docker-compose down --remove-orphans  
docker-compose up -d
```

### Services

The services are available at:
```
Chain simulator: 127.0.0.1:8085
Elasticsearch:   127.0.0.1:9200
API instance:    127.0.0.1:3001
Explorer:        127.0.0.1:3002
Lite Wallet:     127.0.0.1:3003
```

You can find a `test-pem.pem` file inside the `chain-simulator/scripts` directory. It can be used for connecting to Lite Wallet. 
In order to fund it, you have to run the `chain-simulator/scripts/send-tx.sh` script before
