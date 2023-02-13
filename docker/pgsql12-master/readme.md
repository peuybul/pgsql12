#Change Password
ALTER USER postgres PASSWORD 'myPassword';

#Create Replica user
CREATE USER replication REPLICATION LOGIN CONNECTION LIMIT 1 ENCRYPTED PASSWORD 'R3pliC4';
ALTER ROLE replication CONNECTION LIMIT -1;

#Reload Config
su - postgres
/usr/pgsql-12/bin/pg_ctl -D /var/lib/pgsql/12/data/ reload

OR 

SELECT pg_reload_conf();