# GreyNoise Intelligence Alpha API

## Summary:

Grey Noise is a system that collects and analyzes data on Internet-wide scanners. Grey Noise collects data on benign scanners such as Shodan.io, as well as malicious actors like SSH and telnet worms. 

The data is collected by a network of sensors deployed around the Internet in various datacenters, cloud providers, and regions.

## URL: 

```
http://api.greynoise.io:8888/
```

## Endpoints:

* GET /v1/query/list - list all tags
* POST /v1/query/tag - query all IPs that have a given tag
* POST /v1/query/ip - query all tags associated with a given IP

### /v1/query/list

Method: `GET`

Required Parameters: NONE

Example:
```
$ curl -s 'http://api.greynoise.io:8888/v1/query/list'
{
  "status": "ok",
  "tags": [
    "VNC_SCANNER_HIGH",
    "PING_SCANNER_LOW",
    "JBOSS_WORM",
    "GOOGLEBOT",
    "SNMP_SCANNER_LOW",
   ...
    "CPANEL_SCANNER_LOW",
    "WINRM_SCANNER_HIGH",
    "MASSCAN_CLIENT",
    "REDIS_SCANNER_HIGH",
    "RABBITMQ_SCANNER_HIGH"
  ]
}
```

### /v1/query/ip

Method: `POST`

Required Parameters:  

* ip - IP address to query

Optional Parameters:  

* key - A valid API key enables you to receive more than 500 results per query

Example:

```
$ curl -s -XPOST -d 'ip=198.20.69.74' 'http://api.greynoise.io:8888/v1/query/ip'
{
  "ip": "198.20.69.74",
  "status": "ok",
  "returned_count": 500,
  "records": [
    {
      "name": "SHODAN",
      "first_seen": "2017-09-27T02:26:31.957Z",
      "last_updated": "2017-10-19T01:35:34.114Z",
      "confidence": "high",
      "intention": "benign",
      "category": "actor",
      "metadata": {
        "org": "SingleHop, Inc.",
        "rdns": "census1.shodan.io",
        "rdns_parent": "shodan.io",
        "datacenter": "SingleHop",
        "asn": "AS32475",
        "os": "Linux 3.11+",
        "link": "Ethernet or modem",
        "tor": false
      }
   }
}
```

### /v1/query/tag

Method: `POST`

Required Parameters:

* tag - Which tag to query

Optional Parameters:

* key - A valid API key enables you to receive more than 500 results per query

Example:

```
$ curl -s -XPOST -d 'tag=SHODAN' http://api.greynoise.io:8888/v1/query/tag | jq '.'
{
  "tag": "YANDEX_SEARCH_ENGINE",
  "status": "ok",
  "records": [
    {
      "ip": "71.6.158.166",
      "name": "SHODAN",
      "first_seen": "2017-09-27T02:26:31.957Z",
      "last_updated": "2017-10-19T01:35:34.114Z",
      "confidence": "high",
      "intention": "benign",
      "category": "actor",
      "metadata": {
        "org": "SingleHop, Inc.",
        "rdns": "census1.shodan.io",
        "rdns_parent": "shodan.io",
        "datacenter": "SingleHop",
        "asn": "AS32475",
        "os": "Linux 3.11+",
        "link": "Ethernet or modem",
        "tor": false
    },
    {
      "ip": "71.6.158.167",
      "name": "SHODAN",
      "first_seen": "2017-09-27T02:26:31.957Z",
      "last_updated": "2017-10-19T01:35:34.114Z",
      "confidence": "high",
      "intention": "benign",
      "category": "actor",
      "metadata": {
        "org": "SingleHop, Inc.",
        "rdns": "census2.shodan.io",
        "rdns_parent": "shodan.io",
        "datacenter": "SingleHop",
        "asn": "AS32475",
        "os": "Linux 3.11+",
        "link": "Ethernet or modem",
        "tor": false
      }
   }
}
```

## Stats

The following is a snapshot of the data (updated Jan 1, 2018):
```
                    tag_name                    |                     tag_id                     | confidence |   category    |  count
------------------------------------------------+------------------------------------------------+------------+---------------+---------
 SMB Scanner                                    | SMB_SCANNER_LOW                                | low        | activity      | 3112176
 Telnet Scanner                                 | TELNET_SCANNER_LOW                             | low        | activity      | 2842075
 Residential                                    | RESIDENTIAL                                    | high       | hosting       | 1624145
 Telnet Worm                                    | TELNET_WORM_HIGH                               | high       | worm          | 1570835
 Mirai                                          | MIRAI                                          | high       | worm          | 1234927
 Web Scanner                                    | WEB_SCANNER_LOW                                | low        | activity      |  818585
 Web Crawler                                    | WEB_CRAWLER                                    | high       | activity      |  714465
 HTTP Alt Scanner                               | HTTP_ALT_SCANNER_LOW                           | low        | activity      |  629490
 SMB Scanner                                    | SMB_SCANNER_HIGH                               | high       | activity      |  520091
 Telnet Scanner                                 | TELNET_SCANNER_HIGH                            | high       | activity      |  369283
 SSH Scanner                                    | SSH_SCANNER_LOW                                | low        | activity      |  353890
 SSH Worm                                       | SSH_WORM_LOW                                   | low        | worm          |  143587
 SSH Worm                                       | SSH_WORM_HIGH                                  | high       | worm          |  143389
 MSSQL Scanner                                  | MSSQL_SCANNER_LOW                              | low        | activity      |   84416
 Ping Scanner                                   | PING_SCANNER_LOW                               | low        | activity      |   75624
 SSH Scanner                                    | SSH_SCANNER_HIGH                               | high       | activity      |   73920
 DNS Scanner                                    | DNS_SCANNER_LOW                                | low        | activity      |   69208
 FTP Scanner                                    | FTP_SCANNER_LOW                                | low        | activity      |   52201
 Web Scanner                                    | WEB_SCANNER_HIGH                               | high       | activity      |   51608
 RDP Scanner                                    | RDP_SCANNER_LOW                                | low        | activity      |   50376
 ZMap Client                                    | ZMAP_CLIENT                                    | high       | tool          |   37843
 HTTP Alt Scanner                               | HTTP_ALT_SCANNER_HIGH                          | high       | activity      |   37562
 Ethereum Node Scanner                          | ETHEREUM_NODE_SCANNER_LOW                      | low        | activity      |   32402
 Open Proxy Scanner                             | OPEN_PROXY_SCANNER                             | high       | activity      |   30189
 MSSQL Scanner                                  | MSSQL_SCANNER_HIGH                             | high       | activity      |   30158
 SMTP Scanner                                   | SMTP_SCANNER_LOW                               | low        | activity      |   28713
 RDP Scanner                                    | RDP_SCANNER_HIGH                               | high       | activity      |   27424
 NTP Scanner                                    | NTP_SCANNER_LOW                                | low        | activity      |   27130
 Telnet Worm                                    | TELNET_WORM_LOW                                | low        | worm          |   23368
 Ping Scanner                                   | PING_SCANNER_HIGH                              | high       | activity      |   14940
 Squid Proxy Scanner                            | SQUID_PROXY_SCANNER_LOW                        | low        | activity      |   14927
 Drupal CVE-2018-7600 Worm                      | DRUPAL_CVE_2018_7600_WORM                      | high       | worm          |   14271
 PHPMyAdmin Worm                                | PHPMYADMIN_WORM                                | high       | worm          |   13452
 DNS Scanner                                    | DNS_SCANNER_HIGH                               | high       | activity      |   11862
 VNC Scanner                                    | VNC_SCANNER_LOW                                | low        | activity      |   11811
 NTP Scanner                                    | NTP_SCANNER_HIGH                               | high       | activity      |   11258
 CGI Script Scanner                             | CGI_SCRIPT_SCANNER                             | low        | scanner       |   11234
 Router RPC Scanner                             | ROUTER_RPC_SCANNER_LOW                         | low        | activity      |    9457
 MySQL Scanner                                  | MYSQL_SCANNER_LOW                              | low        | activity      |    9412
 Redis Scanner                                  | REDIS_SCANNER_LOW                              | low        | activity      |    8785
 Unknown Linux Worm                             | UNKNOWN_LINUX_WORM                             | high       | worm          |    8561
 Go HTTP Client                                 | GO_HTTP_CLIENT                                 | high       | tool          |    8466
 MySQL Scanner                                  | MYSQL_SCANNER_HIGH                             | high       | activity      |    8025
 VOIP Scanner                                   | VOIP_SCANNER_HIGH                              | high       | activity      |    7887
 SSDP/UPNP Scanner                              | SSDP_UPNP_SCANNER_LOW                          | low        | activity      |    7457
 VOIP Scanner                                   | VOIP_SCANNER_LOW                               | low        | activity      |    7286
 PycURL HTTP Client                             | PYCURL_HTTP_CLIENT                             | high       | tool          |    7258
 Wordpress Worm                                 | WORDPRESS_WORM                                 | medium     | worm          |    7162
 D-Link 2750B Worm                              | DLINK_2750B_WORM                               | high       | worm          |    6340
 SMTP Scanner                                   | SMTP_SCANNER_HIGH                              | high       | activity      |    6139
 FTP Bruteforcer                                | FTP_BRUTEFORCER                                | high       | activity      |    6135
 Redis Scanner                                  | REDIS_SCANNER_HIGH                             | high       | activity      |    5996
 Oracle WebLogic CVE-2017-10271 Worm            | ORACLE_WEBLOGIC_CVE_2017_10271_WORM            | high       | worm          |    5511
 NETBIOS Scanner                                | NETBIOS_SCANNER_LOW                            | low        | activity      |    5489
 VNC Scanner                                    | VNC_SCANNER_HIGH                               | high       | activity      |    5386
 POP3 Scanner                                   | POP3_SCANNER_LOW                               | low        | activity      |    4928
 MSSQL Bruteforcer                              | MSSQL_BRUTEFORCER                              | high       | activity      |    4634
 IMAP Scanner                                   | IMAP_SCANNER_LOW                               | low        | activity      |    4503
 Stretchoid.com                                 | STRETCHOID                                     | high       | actor         |    4034
 FTP Scanner                                    | FTP_SCANNER_HIGH                               | high       | activity      |    3975
 SOCKS Proxy Scanner                            | SOCKS_PROXY_SCANNER_LOW                        | low        | activity      |    3789
 SSDP/UPNP Scanner                              | SSDP_UPNP_SCANNER_HIGH                         | high       | activity      |    3761
 GPON CVE-2018-10561 Router Worm                | GPON_CVE_2018_10561_ROUTER_WORM                | high       | worm          |    3550
 Elasticsearch Scanner                          | ELASTICSEARCH_SCANNER_LOW                      | low        | activity      |    3350
 Windows RDP Cookie Hijacker CVE-2014-6318      | WINDOWS_RDP_COOKIE_HIJACKER_CVE_2014_6318      | high       | worm          |    3242
 LDAP Scanner                                   | LDAP_SCANNER_LOW                               | low        | activity      |    3201
 POP3 Scanner                                   | POP3_SCANNER_HIGH                              | high       | activity      |    3143
 Postgres Scanner                               | POSTGRES_SCANNER_LOW                           | low        | activity      |    3045
 CPanel Scanner                                 | CPANEL_SCANNER_LOW                             | low        | activity      |    3034
 IMAP Scanner                                   | IMAP_SCANNER_HIGH                              | high       | activity      |    3017
 Embedded Device Worm                           | EMBEDDED_DEVICE_WORM                           | high       | worm          |    2918
 Router RPC Scanner                             | ROUTER_RPC_SCANNER_HIGH                        | high       | activity      |    2904
 Dockerd Scanner                                | DOCKERD_SCANNER_LOW                            | low        | activity      |    2815
 ADB Worm                                       | ADB_WORM                                       | high       | worm          |    2719
 IIS WebDAV Remote Code Execution CVE-2017-7269 | IIS_WEBDAV_REMOTE_CODE_EXECUTION_CVE_2017_7269 | high       | worm          |    2671
 CounterStrike Server Scanner                   | COUNTERSTRIKE_SERVER_SCANNER_LOW               | low        | activity      |    2610
 MongoDB Scanner                                | MONGODB_SCANNER_LOW                            | low        | activity      |    2562
 NETBIOS Scanner                                | NETBIOS_SCANNER_HIGH                           | high       | activity      |    2498
 CPanel Scanner                                 | CPANEL_SCANNER_HIGH                            | high       | activity      |    2327
 Belkin N750 Worm CVE-2014-1635                 | BELKIN_N750_WORM_CVE_2014_1635                 | high       | worm          |    2237
 Dockerd Scanner                                | DOCKERD_SCANNER_HIGH                           | high       | activity      |    2234
 Bitcoin Node Scanner                           | BITCOIN_NODE_SCANNER_LOW                       | low        | activity      |    2192
 Memcached Scanner                              | MEMCACHED_SCANNER_LOW                          | low        | activity      |    2106
 PPTP VPN Scanner                               | PPTP_VPN_SCANNER_LOW                           | low        | activity      |    2082
 Privoxy Proxy Scanner                          | PRIVOXY_PROXY_SCANNER_LOW                      | low        | activity      |    1972
 Elasticsearch Scanner                          | ELASTICSEARCH_SCANNER_HIGH                     | high       | activity      |    1969
 Postgres Scanner                               | POSTGRES_SCANNER_HIGH                          | high       | activity      |    1915
 Jboss Worm                                     | JBOSS_WORM                                     | medium     | worm          |    1871
 Squid Proxy Scanner                            | SQUID_PROXY_SCANNER_HIGH                       | high       | activity      |    1869
 LDAP Scanner                                   | LDAP_SCANNER_HIGH                              | high       | activity      |    1832
 Siemens PLC Scanner                            | SIEMENS_PLC_SCANNER_LOW                        | low        | activity      |    1804
 CounterStrike Server Scanner                   | COUNTERSTRIKE_SERVER_SCANNER_HIGH              | high       | activity      |    1722
 Jorgee HTTP Scanner                            | JORGEE_HTTP_SCANNER                            | high       | tool          |    1711
 MongoDB Scanner                                | MONGODB_SCANNER_HIGH                           | high       | activity      |    1703
 Python Requests Client                         | PYTHON_REQUESTS_CLIENT                         | high       | tool          |    1672
 SOCKS Proxy Scanner                            | SOCKS_PROXY_SCANNER_HIGH                       | high       | activity      |    1608
 SNMP Scanner                                   | SNMP_SCANNER_LOW                               | low        | activity      |    1569
 IPSec VPN Scanner                              | IPSEC_VPN_SCANNER_LOW                          | low        | activity      |    1529
 Cassandra Scanner                              | CASSANDRA_SCANNER_LOW                          | low        | activity      |    1527
 GoogleBot                                      | GOOGLEBOT                                      | high       | search_engine |    1506
 Memcached Scanner                              | MEMCACHED_SCANNER_HIGH                         | high       | activity      |    1474
 RabbitMQ Scanner                               | RABBITMQ_SCANNER_LOW                           | low        | activity      |    1462
 Tor                                            | TOR                                            | high       | hosting       |    1401
 NetCraft                                       | NETCRAFT                                       | high       | actor         |    1334
 SNMP Scanner                                   | SNMP_SCANNER_HIGH                              | high       | activity      |    1288
 PPTP VPN Scanner                               | PPTP_VPN_SCANNER_HIGH                          | high       | activity      |    1263
 Netis Router Admin Scanner                     | NETIS_ROUTER_ADMIN_SCANNER_HIGH                | high       | activity      |    1138
 Siemens PLC Scanner                            | SIEMENS_PLC_SCANNER_HIGH                       | high       | activity      |    1119
 IOT MQTT Scanner                               | IOT_MQTT_SCANNER_LOW                           | low        | activity      |    1095
 Netis Router Admin Scanner                     | NETIS_ROUTER_ADMIN_SCANNER_LOW                 | low        | activity      |     925
 Printer Scanner                                | PRINTER_SCANNER_LOW                            | low        | activity      |     911
 D-Link 850L Worm                               | DLINK_850L_WORM                                | high       | worm          |     866
 Privoxy Proxy Scanner                          | PRIVOXY_PROXY_SCANNER_HIGH                     | high       | activity      |     853
 Cassandra Scanner                              | CASSANDRA_SCANNER_HIGH                         | high       | activity      |     831
 BingBot                                        | BINGBOT                                        | high       | search_engine |     830
 WinRM Scanner                                  | WINRM_SCANNER_LOW                              | low        | activity      |     822
 VNC Bruteforcer                                | VNC_BRUTEFORCER                                | high       | activity      |     818
 Compromised Raspberry Pi                       | COMPROMISED_RASPBERRY_PI                       | high       | worm          |     805
 RabbitMQ Scanner                               | RABBITMQ_SCANNER_HIGH                          | high       | activity      |     754
 LiteCoin Node Scanner                          | LITECOIN_NODE_SCANNER_LOW                      | low        | activity      |     747
 BinaryEdge.io                                  | BINARYEDGE                                     | high       | actor         |     728
 Ethereum Node Scanner                          | ETHEREUM_NODE_SCANNER_HIGH                     | high       | activity      |     664
 IOT MQTT Scanner                               | IOT_MQTT_SCANNER_HIGH                          | high       | activity      |     541
 CHINANET SSH Bruteforcer                       | CHINANET_SSH_BRUTEFORCER                       | high       | worm          |     539
 TFTP Scanner                                   | TFTP_SCANNER_LOW                               | low        | activity      |     530
 Nmap                                           | NMAP                                           | high       | tool          |     522
 Minecraft Scanner                              | MINECRAFT_SCANNER_LOW                          | low        | activity      |     504
 Bitcoin Node Scanner                           | BITCOIN_NODE_SCANNER_HIGH                      | high       | activity      |     457
 Masscan Client                                 | MASSCAN_CLIENT                                 | high       | tool          |     452
 Ahrefs                                         | AHREFS                                         | high       | actor         |     448
 Cobalt Strike Scanner                          | COBALT_STRIKE_SCANNER_LOW                      | low        | activity      |     442
 TFTP Scanner                                   | TFTP_SCANNER_HIGH                              | high       | activity      |     424
 IPSec VPN Scanner                              | IPSEC_VPN_SCANNER_HIGH                         | high       | activity      |     420
 Printer Scanner                                | PRINTER_SCANNER_HIGH                           | high       | activity      |     413
 WinRM Scanner                                  | WINRM_SCANNER_HIGH                             | high       | activity      |     406
 ZmEu Worm                                      | ZMEU_WORM                                      | high       | worm          |     405
 Yandex Search Engine                           | YANDEX_SEARCH_ENGINE                           | high       | search_engine |     386
 Censys                                         | CENSYS                                         | medium     | actor         |     337
 Censys                                         | CENSYS                                         | high       | actor         |     321
 Fast HTTP Auth Scanner Client                  | FAST_HTTP_AUTH_SCANNER_CLIENT                  | high       | tool          |     318
 Project Sonar                                  | PROJECT_SONAR                                  | high       | actor         |     306
 University of Michigan                         | UNIVERSITY_OF_MICHIGAN                         | high       | actor         |     284
 PDRLabs.net                                    | PDRLABS                                        | high       | actor         |     282
 Huawei HG532 UPnP Worm CVE-2017-17215          | HUAWEI_HG532_UPNP_WORM_CVE_2017_17215          | high       | worm          |     261
 Realtek Miniigd UPnP Worm CVE-2014-8361        | REALTEK_MINIIGD_UPNP_WORM_CVE_2014_8361        | high       | worm          |     256
 MJ12bot                                        | MJ12BOT                                        | high       | actor         |     253
 ShadowServer.org                               | SHADOWSERVER                                   | high       | actor         |     228
 Minecraft Scanner                              | MINECRAFT_SCANNER_HIGH                         | high       | activity      |     209
 Zyxel OS Command Injection CVE-2017-6884       | ZYXEL_OS_COMMAND_INJECTION_CVE_2017_6884       | high       | worm          |     164
 Java HTTP Client                               | JAVA_HTTP_CLIENT                               | high       | tool          |     160
 Go SSH Scanner                                 | GO_SSH_SCANNER                                 | high       | tool          |     157
 Ping Scanner                                   | PING_SCANNER_LOW                               | high       | activity      |     151
 Wordpress XML RPC Worm                         | WORDPRESS_XML_RPC_WORM                         | high       | worm          |     135
 ipip.net                                       | IPIP                                           | high       | actor         |     134
 ONYPHE                                         | ONYPHE                                         | high       | actor         |     111
 Internet Census                                | INTERNET_CENSUS                                | high       | actor         |      99
 LiteCoin Node Scanner                          | LITECOIN_NODE_SCANNER_HIGH                     | high       | activity      |      83
 Cobalt Strike Scanner                          | COBALT_STRIKE_SCANNER_HIGH                     | high       | activity      |      81
 Net Systems Research                           | NET_SYSTEMS_RESEARCH                           | high       | actor         |      79
 Uptime.com                                     | UPTIME                                         | high       | actor         |      60
 Baidu Spider                                   | BAIDU_SPIDER                                   | high       | search_engine |      60
 ZGrab SSH Scanner                              | ZGRAB_SSH_SCANNER                              | high       | tool          |      59
 Mail.RU                                        | MAIL_RU                                        | high       | actor         |      49
 Seznam                                         | SEZNAM                                         | high       | actor         |      47
 Facebook NetProbe                              | FACEBOOK_NETPROBE                              | high       | actor         |      43
 DataProvider                                   | DATAPROVIDER                                   | high       | actor         |      41
 Elasticsearch Scanner                          | ELASTICSEARCH_SCANNER                          | low        | activity      |      36
 Hadoop Yarn Worm                               | HADOOP_YARN_WORM                               | high       | worm          |      35
 Sogou                                          | SOGOU                                          | high       | actor         |      34
 Cloud System Networks                          | CLOUD_SYSTEM_NETWORKS                          | high       | actor         |      32
 Shodan.io                                      | SHODAN                                         | high       | actor         |      30
 Postgres Bruteforcer                           | POSTGRES_BRUTEFORCER                           | high       | activity      |      30
 SEMrush                                        | SEMRUSH                                        | high       | actor         |      19
 DomainTools                                    | DOMAINTOOLS                                    | high       | actor         |      17
 Moz DotBot                                     | MOZ_DOTBOT                                     | high       | actor         |      14
 PHP Worm                                       | PHP_WORM                                       | high       | worm          |      14
 SafeDNS                                        | SAFEDNS                                        | high       | actor         |      12
 WhatWeb Scanner                                | WHATWEB_SCANNER                                | high       | tool          |      12
 RWTH AACHEN University                         | RWTH_AACHEN_UNIVERSITY                         | high       | actor         |      11
 Ruhr-Universitat Bochum                        | RUHR_UNIVERSITTT_BOCHUM                        | high       | actor         |      10
 Quadmetrics.com                                | QUADMETRICS                                    | high       | actor         |      10
 Pingdom.com                                    | PINGDOM                                        | high       | actor         |       9
 Linksys E-Series TheMoon Router Worm           | LINKSYS_E_SERIES_THEMOON_ROUTER_WORM           | high       | worm          |       8
 ExposureMonitoring                             | EXPOSURE_MONITORING                            | high       | actor         |       8
 Avtech IP Camera Worm                          | AVTECH_IP_CAMERA_WORM                          | high       | worm          |       8
 Eir D1000 Router Worm                          | EIR_D1000_ROUTER_WORM                          | high       | worm          |       7
 Qwant                                          | QWANT                                          | high       | actor         |       7
 Asterisk Bruteforcer                           | ASTERISK_BRUTEFORCER                           | high       | activity      |       7
 CheckMarkNetwork                               | CHECKMARKNETWORK                               | high       | actor         |       7
 Intrinsec                                      | INTRINSEC                                      | high       | actor         |       6
 LINK-NET LW-N605R Worm CVE-2018-16752          | LINK_NET_LW_N605R_WORM_CVE_2018_16752          | high       | worm          |       6
 PingZapper                                     | PINGZAPPER                                     | high       | actor         |       6
 WinRM Scanner                                  | WinRM_SCANNER_LOW                              | low        | activity      |       5
 IBM oBot                                       | IBM_OBOT                                       | high       | actor         |       5
 OpenLinkProfiler                               | OPENLINKPROFILER                               | high       | actor         |       5
 CCBot                                          | CCBOT                                          | high       | actor         |       5
 Coc Coc                                        | COCCOC                                         | high       | actor         |       5
 Brown University                               | BROWN_UNIVERSITY                               | high       | actor         |       4
 Riddler.io                                     | RIDDLER                                        | high       | actor         |       4
 University of New Mexico                       | UNIVERSITY_OF_NEW_MEXICO                       | high       | actor         |       4
 Unauthenticated Redis Worm                     | UNAUTHENTICATED_REDIS_WORM                     | high       | worm          |       4
 Project25499                                   | PROJECT25499                                   | high       | actor         |       3
 Team Cymru                                     | TEAM_CYMRU                                     | high       | actor         |       3
 Talaia                                         | TALAIA                                         | high       | actor         |       3
 ProxyBroker                                    | PROXYBROKER                                    | high       | tool          |       3
 Cliqz                                          | CLIQZ                                          | high       | actor         |       2
 University of California Berkeley              | UNIVERSITY_OF_CALIFORNIA_BERKELEY              | high       | actor         |       2
 CyberGreen                                     | CYBERGREEN                                     | high       | actor         |       2
 CompanyBook                                    | COMPANYBOOK                                    | high       | actor         |       2
 Panscient                                      | PANSCIENT                                      | high       | actor         |       2
 Archive.org                                    | ARCHIVE                                        | high       | actor         |       2
 Ampere Innotech                                | AMPERE_INNOTECH                                | high       | actor         |       2
 aiHit                                          | AIHIT                                          | high       | actor         |       2
 LoSec                                          | LOSEC                                          | high       | actor         |       1
 Statastico                                     | STATASTICO                                     | high       | actor         |       1
 MauiBot                                        | MAUIBOT                                        | high       | actor         |       1
 SiteExplorer                                   | SITEEXPLORER                                   | high       | actor         |       1
 Mojeek                                         | MOJEEK                                         | high       | actor         |       1
 FindMalware                                    | FINDMALWARE                                    | high       | actor         |       1
 ProbeTheNet.com                                | PROBETHENET                                    | high       | actor         |       1
 Cambridge Cybercrime Centre                    | CAMBRIDGE_CYBERCRIME_CENTRE                    | high       | actor         |       1
 A10 Networks                                   | A10_NETWORKS                                   | high       | actor         |       1
 Stanford University                            | STANFORD_UNIVERSITY                            | high       | actor         |       1
```
