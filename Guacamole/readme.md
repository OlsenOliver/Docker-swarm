There are several steps to get this stack running properly.

Firstly, add secrets in Swarm for the mysql user as well as root user. Call these files guac_db_root_pass and guac_db_user_pass. Save these secrets in a key vault or something as you will not be able to retreive those when saved (except for accessing the DB-container and check the /run/secrets-files).

Then run 
docker stack deploy -c guacamole-stack-init.yml guacamole

This will deploy MariaDB. 

To retrieve the database you will need for Guacamole, run the following command

docker run --rm guacamole/guacamole:1.4.0 /opt/guacamole/bin/initdb.sh --mysql > initdb.sql


Find the ID of MariaDB when successfully deployed and run the following

docker cp initdb.sql guacamoledb:/initdb.sql [substitute guacamoledb with the ID of the container]

Then
docker exec -it guacamoledb bash
cat /initdb.sql | mysql -u root -p guacamole_db
exit

Now you should have a fully functional MariaDB with the database for Guacamole.
