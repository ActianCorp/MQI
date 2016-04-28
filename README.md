# MQI
##Command line utility for  running scripts and commands across a cluster
###(particularly aimed at VectorH and Matrix/ParAccel)

####Overview
This Linux BASH script was initially developed to provide a mechanism by which commands could be invoked from a single node in a Vector in Hadoop (aka VectorH or Vortex) or Matrix (aka ParAccel or PADB) cluster.  The results of which would then be picked up within the Actian Services' Enterprise Monitoring Appliance (EMA) - a solution developed to provide monitoring and alerting of Actian's products and based on the Nagios framework.
####Usage
```
  mqi
      -p|--platform M|V|L        Matrix|Vector|List
      -s|--ii_system II_SYSTEM   Path to II_SYSTEM
      -allx command              Run command on node(s)
      -cmp file                  Compare file across node(s)
      -cpall                     Copy file to node(s)
      -ping                      Ping node
      -o|--output file           Send output to file
      -a address                 Only on one node
      -v                         Verbose
```
####Examples
```
mqi -p V -s /opt/Actian/VectorX1 -v -allx "hostname"

  Remote Node: 172.16.68.2
  padb-cluster2
  
  Remote Node: 172.16.68.3
  padb-cluster3
  
  Remote Node: 172.16.68.4
  padb-cluster4
  
  Local Node: 172.16.68.5
  padb-cluster5
  
  Remote Node: 172.16.68.6
  padb-cluster6
  
  Remote Node: 172.16.68.7
  padb-cluster7
```

```
mqi -p V -s /opt/Actian/VectorX1 -v -allx "export TERM=xterm; top -n 1 | grep Mem:"
  
  Remote Node: 172.16.68.2
  Mem:  198297500k total, 196195772k used,  2101728k free,  1845628k buffers
  
  Remote Node: 172.16.68.3
  Mem:  198297500k total, 196194000k used,  2103500k free,  1845628k buffers
  
  Remote Node: 172.16.68.4
  Mem:  198297500k total, 196194212k used,  2103288k free,  1845628k buffers
  
  Local Node: 172.16.68.5
  Mem:  198297500k total, 196195752k used,  2101748k free,  1845628k buffers
  
  Remote Node: 172.16.68.6
  Mem:  198297500k total, 196196256k used,  2101244k free,  1845628k buffers
  
  Remote Node: 172.16.68.7
  Mem:  198297500k total, 196204588k used,  2092912k free,  1845628k buffers
```

