## 1.服务端

mkdir /home/work

vi /etc/exports

/home/work 192.168.64.*(rw,sync,no_root_squash)

## 2.服务端 客户端

yum install nfs rpcbind

## 3.测试重启

[root@M1 ]# /etc/init.d/nfs restart 

[root@M1 ]# /etc/init.d/rpcbind restart 

## 4.服务端

[root@M1 ~]# exportfs 

/home/work    	192.168.64.*

## 5.客户端挂载

mount -t nfs -o rw 服务端:/路径/ /客户端挂载路径/

## 6.自启动

echo "/etc/init.d/nfs start " >> /etc/rc.d/rc.local

echo "/etc/init.d/rpcbind start" >> /etc/rc.d/rc.local

echo "mount -t nfs -o rw 192.168.64.132:/home/work/ /data/" >> /etc/rc.d/rc.local 
