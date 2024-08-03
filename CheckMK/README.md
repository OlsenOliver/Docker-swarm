CheckMK does require FIFO to be available, and in my setup I use NFS ad backend, thus the container will not work.
As a poor man's workaround I decided to run this container on one of my nodes in the cluster, but with a local bind mount.
Far from ideal, but I don't have the hardware to configure a Ceph-cluster only for this purpose.