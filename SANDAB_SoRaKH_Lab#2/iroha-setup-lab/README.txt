1. Unpack the the zip file
2. Run docker-compose up -d
3. Run docker ps
4. Get one container id of iroha-node in the list
5. Run docker exec -it <container id> bash
6. Run iroha-cli -account_name root@sorakh (login as root to add asset and transfer asset to bob's account)
7. Then add asset quantity and transfer to bob's account 
8. Run iroha-cli -account_name bob@sorakh 
9. Add Signatory by input alice's public key
10. Grant permission by input permission name: can_transfer
11. Finally alice can transfer bob's asset