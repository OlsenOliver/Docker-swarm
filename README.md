# Docker-swarm
 Compose-files for use with Docker Swarm. 
 These are compose-files I use in my own Docker-swarm setup, and for simplicity I tend to use NFS for shared storage. For use in your own environment you will need to fill in the correct IP for your NFS backend/NAS as well as adjusting the name of the share and folders.

 I don't like having passwords in separate environment-files or directly in the compose-files, so you will need to create Docker secrets to apply these files.
 If you use a single node Swarm you will need to remove the placement constraints or change the role from 'worker' to 'manager'
