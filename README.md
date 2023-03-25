
# MPF (modular policy framework)
 * It is used to define set of rules applying firewall features, such as traffic inspection, QoS etc. to the traffic transiting the firewall.

 * Class-ma p for traffic inspection:
 
      - Global policy
      - interface policy(in/out)
      
![image](https://user-images.githubusercontent.com/128924924/227733297-01f7cbf2-acd6-497a-a215-0fba58b29b6c.png)

![image](https://user-images.githubusercontent.com/128924924/227733361-50020eb9-f9bc-4468-a1c9-b5be20538002.png)


![image](https://user-images.githubusercontent.com/128924924/227733394-929cc65f-a784-4ad8-b721-8306ee033c63.png)


![image](https://user-images.githubusercontent.com/128924924/227733418-67466f47-e7df-4744-9527-5779b4fd0dc9.png)


# LAB 

![image](https://user-images.githubusercontent.com/128924924/227733455-5ebfaed5-e398-492b-8aa1-24f814e567a9.png)


Do all the basic config in devices include route

Assume 200.10.10.1 is R2
Assume 192.168.1.1 is R1
* Create telnet in R2 and access it from R1 . its work 
* Ping R1to R2 its not work

# #f03c15 ERROR:
(suppose we ping from R1 to R2 its fail. Return traffic is blocked in fw becz connection table not store the traffic . normally we enable icmp,we can use another methode)

FW
```
Access-list myacl permit icmp any any
Class-map my class
Match access-list myacl
Exit
Policy-map mypolicy
Class myclass
Inspect icmp
Police input 8000 conform-action transmit exceed-action drop
Exit
```
# Now I want to apply this in interface not globally

    Service-policy my policy interface outside


# we want to allow the icmp reply from outside to inside”

Now ping from R1 to R2 its work :

Check service-policy

    show service-policy



