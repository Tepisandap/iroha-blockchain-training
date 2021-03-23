1. Unpack the the zip file
2. Run docker volume prune -f
3. Run docker-compose up -d
4. Run docker ps
5. Get one container id of iroha-node in the list
6. Run docker exec -it <container id> bash
7. iroha-cli -account_name root@sorakh