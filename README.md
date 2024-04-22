# Docker-swarm
My compose-files for use with Docker Swarm. 
 These are compose-files I use in my own Docker-swarm setup, and for simplicity I tend to use TrueNAS/NFS for shared storage. 
 For use in your own environment you will need to fill in the correct IP for your NFS backend/NAS as well as adjusting the name of the share and folders. Depending on your own setup you might want to change the exposed ports. I have not been too consistent in specifying release tags in my compose-files, but for unwanted upgrades I suggest you tune this to your own need and preferences.

In a few stacks I have also used Docker secrets to avoid having passwords in the compose or environment-file. Not all images support this, so YMMV...

If you use a single node Swarm you will need to remove the placement constraints or change the role from 'worker' to 'manager'
