## Atividades Métricas

**SNMP Atividade** 

**Engenharia da Computação** 

* Com o Ubuntu mini que vocês já possuem eu seu VirtualBox, seguir com o os passos descritos na atividade abaixo: 

* Instalar snmp no Ubuntu mini (usuário e senha: satc): 


* `$ sudo su` (senha satc) 


* `# apt-get update` 


* `# apt-get install snmpd*` 


* `# apt-get install snmp-mibs-downloader` (traduz os OIDs em nome amigável) 


* `# vi /etc/snmp/snmp.conf` (Comentar linux mibs: com '#' em seguida acrescentar abaixo 'mibs +ALL', ':x' salvar e sair) 


* `# vi /etc/snmp/snmpd.conf` (habilitar linha rocommunity public) 


* `# /etc/init.d/snmpd restart` 


* `#snmpwalk -v 1 -c public localhost` (Observar as MIBs) 

---
 
**SNMP Atividade** 

**Engenharia da Computação** 


* Algumas MIBs são importantes para métricas de informações de CPU, como `UCD-SNMP-MIB::laLoad`. 


* Utilize os comandos `snmptranslate`, `snmpwalk`, `snmpget` e `snmptable` para apresentar o que descobriu sobre esta MIB. 


* Trabalho individual, entrega em formato de video mostrando os comandos em tempo de execução e devidos retornos. 


* Pode ocorrer um erro de MIB `"Bad operator (INTEGER): At line 73 in /usr/share/mibs/ietf/SNMPv2-PDU Unlinked OID in "`, devido a um patch problemático. 


* Para isso digite os comandos abaixo para atualizar a BASE MIB sem estes problemas. 


* `http://www.iana.org/assignments/ianaippmmetricsregistry-mib/ianaippmmetricsregistry-mib -0 /var/lib/snmp/mibs/iana/IANA-IPPM-` 


* `$ sudo wget METRICS-REGISTRY-MIB` 


* `$ sudo wget http://pastebin.com/raw.php?i=p3QyuXzZ -0 /usr/share/snmp/mibs/ietf/SNMPv2-PDU` 


* `$ sudo wget http://pastebin.com/raw.php?i=gG7j8nyk -0 /usr/share/snmp/mibs/ietf/IPATM-IPMC-MIB`