Step #1: Pull iroha image
docker pull hyperledger/iroha:latest

Step #2: Create iroha block store
docker volume create blockstore

Step #3: Create docker network for iroha
docker network create iroha-network

Step #4: Pull postgres
docker pull postgres:9.5

Step #5: Create iroha postgres db
docker run --name some-postgres \
-e POSTGRES_USER=postgres \
-e POSTGRES_PASSWORD=mysecretpassword \
-p 5432:5432 --network=iroha-network -d postgres:9.5

Step #6: Prepare config (config.docker, genesis.block, node0.priv, node0.pub, admin@test.priv, admin@test.pub, test@test.priv, test@test.pub)

Step #7: Let run iroha node
docker run -d --name iroha \
-p 50051:50051 \
-v /Users/sakadahuong/Sakada/iroha-training/iroha-setup/config:/opt/iroha_data \
-v blockstore:/tmp/block_store \
-e POSTGRES_HOST='some-postgres' \
-e POSTGRES_PORT='5432' \
-e POSTGRES_PASSWORD='mysecretpassword' \
-e POSTGRES_USER='postgres' \
-e KEY='node0' \
--network=iroha-network \
hyperledger/iroha:latest

Step #8: Interact with iroha by iroha-cli inside docker container
iroha-cli -account_name [name@domain]