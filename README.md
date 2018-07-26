##NFS High availability with Failover

#Setup:
1 Webserver
2 NFS Master servers

#Config:
Webserver document root is mounted with one NFS master mount point. /etc/fstab contains both entries for NFS master.

cat /etc/fstab
LABEL=cloudimg-rootfs	/	 ext4	defaults,discard	0 0
172.31.25.48:/data/stag /mnt/data/stag nfs     defaults        0       0
#172.31.25.3:/data/stag /mnt/data/stag nfs     defaults        0       0


#Scenario:
Suppose one of the master NFS is down, the script will auto mount the NFS Master 2 server. And once the NFS Master 1 is up, it will mount the NFS Master 1 again.
