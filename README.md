# g3m
C Tool to test resilience and DDoS mitigation capability of an internet connected server

## Compiling
### Default:
`gcc g3m.c -o g3m`

## Usage
`g3m [OPTIONS] -h <destination HOST or IP> -p <startPort>,<endPort>`

### Options
```
-T TCP attack [0:ACK, 1:FIN, 2:RST, 3:SYN]   (no default)  
-U UDP attack                                (no options)  
-I ICMP attack                               (no options)  
-N Bogus No flag attack                      (no options)  
-s source class/ip                           (defaults to random )  
-h destination host/ip                       (no default)  
-d destination class                         (no default)  
-p destination port range [start,end]        (defaults to random )  
-q source port range [start,end]             (defaults to random )  
-l % of box link to use                      (defaults to 100%)  
-t timeout                                   (defaults to forever)  
```

### Examples
`g3m -T 3 -I -h 192.168.25.155 -p 80,80` *Performing a TCP SYN and ICMP Flood at port 80 of 192.168.25.155.*  
`g3m -U -h 192.168.25.100 -p 7171,7174` *UDP attack at ports 7171, 7172, 7173 and 7174 of 192.168.25.100*  
`g3m -T 2 -s 5.5.5.5 -h 192.168.25.100` *TCP RST Attack at Random port, setting source ip header field with 5.5.5.5*
