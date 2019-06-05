
    操作:
    - ACCEPT: 讓封包通過
    - DROP: 把封包丟到地上
    - REJECT:  

    table:
    - filter: 做封包的過濾
    - nat: 調整封包來源跟目的地(連接不同網路，需要做位置轉換時)(ipv6無)
    - mangle: 專門針對封包其他欄位做修改
    
    filter table chains:
        - INPUT
        - OUTPUT
        - FORWARD
        
    nat table chains:
        - PREROUTING
        - OUTPUT
        - PREROUTING
    
```

封包傳送過程

-->PREROUTING --> ROUTING DECISION --> FORWARD --> POSTOUT-->
                        ˇ                            ^ 
                        ˇ                            ^     
                        ˇ                          OUTPUT
                        ˇ                            ^
Kernel                INPUT --> LOCAL PROCESS -----> ^
                                (Web Server)
                                
```                            
                                
    1.會進入 INPUT CHAIN 就不會進入 FORWARD CHAIN
    2.會進入 FORWARD CHAIN 的封包 目的地不是防火牆本身
    3.規則由上往下

PARAMETERS

    -A --append 把規則加在最底下
    
    -D --delete
    
    -I --insert 把規則加在指令行間(預設第一行)
    
    -t <table name> 
    
    -L 查看某table狀況

    -p [tcp|udp|icmp|all](可用!表除了xxx之外)
        
    --dport [22] 目的地 port
    
    --sport [22] 來源 port
    
    -s 192.168.0.0/24 來源ip位置
    
    -d 目的地ip位置
    
    -j jump [TARGET|user-defined chain]
    
    -i 接收封包網卡名稱
     
    -o 送出封包網卡名稱
    
    -F [chain] 一次把table規則清掉
    
    -N Create new user-define chain
    
    -P [chain] [target] Set policy for the chain
    
    -R [chain] [rulnum] [rule] replace
    
    
    
ex: iptables -t filter -A INPUT -i eth0 -p tcp --dport 21 -j DROP

    iptables -t filter -A INPUT -i eth0 -p tcp --dport 21 -s 192.168.0.14 -j ACCEPT
    
    iptables -D INPUT 2
    
    iptables -L -n(show ip)
    
    iptables -t filter -A INPUT -i eth0 -p icmp --icmp-type echo-request -j ACCEPT //阻擋人家ping，自己可以ping
    
    iptables -N SSH
    
    iptables -I 4 INPUT -i en0 -p tcp --dport 22 -j SSH
    
    iptables -R SSH 2 -i en0 -p tcp --dport 22 -j REJECT --reject-with icmp -host-unreachable
    
    service iptables save
    
    chkconfig iptables on
    
    
    
    
    
    

一個防火牆的規則分三大部分:
    
    1.iptables -t filter -A INPUT // filter 表中的 INPUT chain
    
    2.-i eth0 -p tcp --dport 21 // 指定封包規格
    
    3.-j DROP //操作
    
    
    
    
    
    
    
    
    

