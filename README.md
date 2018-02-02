# GreyNoise Intelligence Alpha API

## Summary:

GreyNoise is a system that collects and analyzes data on Internet-wide scanners. GreyNoise collects data on benign scanners such as Shodan.io, as well as malicious actors like SSH and telnet worms. 

The data is collected by a network of sensors deployed around the Internet in various datacenters, cloud providers, and regions.

## URL: 

```
https://api.greynoise.io/
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
  "tag": "SHODAN",
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
           tag_name            |              tag_id               | confidence |   category    | count
-------------------------------+-----------------------------------+------------+---------------+--------
 Telnet Scanner                | TELNET_SCANNER_LOW                | low        | activity      | 979176
 SMB Scanner                   | SMB_SCANNER_LOW                   | low        | activity      | 677731
 Telnet Worm                   | TELNET_WORM_HIGH                  | high       | worm          | 556926
 Residential                   | RESIDENTIAL                       | high       | hosting       | 474311
 SMB Scanner                   | SMB_SCANNER_HIGH                  | high       | activity      | 218937
 Mirai                         | MIRAI                             | high       | worm          | 216705
 Telnet Scanner                | TELNET_SCANNER_HIGH               | high       | activity      | 206977
 SSH Scanner                   | SSH_SCANNER_LOW                   | low        | activity      | 121815
 Web Scanner                   | WEB_SCANNER_LOW                   | low        | activity      | 117528
 SSH Worm                      | SSH_WORM_HIGH                     | high       | worm          |  68690
 HTTP Alt Scanner              | HTTP_ALT_SCANNER_LOW              | low        | activity      |  44212
 SSH Scanner                   | SSH_SCANNER_HIGH                  | high       | activity      |  31991
 MSSQL Scanner                 | MSSQL_SCANNER_LOW                 | low        | activity      |  23518
 Ping Scanner                  | PING_SCANNER_LOW                  | low        | activity      |  18986
 SSH Worm                      | SSH_WORM_LOW                      | low        | worm          |  18211
 FTP Scanner                   | FTP_SCANNER_LOW                   | low        | activity      |  15868
 MSSQL Scanner                 | MSSQL_SCANNER_HIGH                | high       | activity      |  15192
 RDP Scanner                   | RDP_SCANNER_LOW                   | low        | activity      |  12739
 DNS Scanner                   | DNS_SCANNER_LOW                   | low        | activity      |  12608
 Telnet Worm                   | TELNET_WORM_LOW                   | low        | worm          |  11638
 Web Scanner                   | WEB_SCANNER_HIGH                  | high       | activity      |  11257
 SMTP Scanner                  | SMTP_SCANNER_LOW                  | low        | activity      |   7127
 NTP Scanner                   | NTP_SCANNER_LOW                   | low        | activity      |   7069
 RDP Scanner                   | RDP_SCANNER_HIGH                  | high       | activity      |   6054
 HTTP Alt Scanner              | HTTP_ALT_SCANNER_HIGH             | high       | activity      |   5227
 Squid Proxy Scanner           | SQUID_PROXY_SCANNER_LOW           | low        | activity      |   4933
 MySQL Scanner                 | MYSQL_SCANNER_LOW                 | low        | activity      |   4382
 Ping Scanner                  | PING_SCANNER_HIGH                 | high       | activity      |   3973
 MySQL Scanner                 | MYSQL_SCANNER_HIGH                | high       | activity      |   3938
 SSDP/UPNP Scanner             | SSDP_UPNP_SCANNER_LOW             | low        | activity      |   3694
 PHPMyAdmin Worm               | PHPMYADMIN_WORM                   | high       | worm          |   3489
 SSDP/UPNP Scanner             | SSDP_UPNP_SCANNER_HIGH            | high       | activity      |   2163
 ZMap Client                   | ZMAP_CLIENT                       | high       | tool          |   2138
 Open Proxy Scanner            | OPEN_PROXY_SCANNER                | high       | activity      |   2101
 Unknown Linux Worm            | UNKNOWN_LINUX_WORM                | high       | worm          |   2007
 Wordpress Worm                | WORDPRESS_WORM                    | medium     | worm          |   1924
 Router RPC Scanner            | ROUTER_RPC_SCANNER_LOW            | low        | activity      |   1861
 VNC Scanner                   | VNC_SCANNER_LOW                   | low        | activity      |   1789
 VOIP Scanner                  | VOIP_SCANNER_HIGH                 | high       | activity      |   1777
 Redis Scanner                 | REDIS_SCANNER_LOW                 | low        | activity      |   1633
 Stretchoid.com                | STRETCHOID                        | high       | actor         |   1591
 Jorgee HTTP Scanner           | JORGEE_HTTP_SCANNER               | high       | tool          |   1503
 FTP Scanner                   | FTP_SCANNER_HIGH                  | high       | activity      |   1496
 VOIP Scanner                  | VOIP_SCANNER_LOW                  | low        | activity      |   1303
 CounterStrike Server Scanner  | COUNTERSTRIKE_SERVER_SCANNER_LOW  | low        | activity      |   1275
 VNC Scanner                   | VNC_SCANNER_HIGH                  | high       | activity      |   1262
 MongoDB Scanner               | MONGODB_SCANNER_LOW               | low        | activity      |   1224
 NTP Scanner                   | NTP_SCANNER_HIGH                  | high       | activity      |   1134
 Tor                           | TOR                               | high       | hosting       |   1133
 DNS Scanner                   | DNS_SCANNER_HIGH                  | high       | activity      |   1088
 Memcached Scanner             | MEMCACHED_SCANNER_LOW             | low        | activity      |   1014
 Embedded Device Worm          | EMBEDDED_DEVICE_WORM              | high       | worm          |   1003
 SOCKS Proxy Scanner           | SOCKS_PROXY_SCANNER_LOW           | low        | activity      |    966
 SNMP Scanner                  | SNMP_SCANNER_LOW                  | low        | activity      |    933
 Router RPC Scanner            | ROUTER_RPC_SCANNER_HIGH           | high       | activity      |    929
 Redis Scanner                 | REDIS_SCANNER_HIGH                | high       | activity      |    926
 Elasticsearch Scanner         | ELASTICSEARCH_SCANNER_LOW         | low        | activity      |    904
 CounterStrike Server Scanner  | COUNTERSTRIKE_SERVER_SCANNER_HIGH | high       | activity      |    840
 MongoDB Scanner               | MONGODB_SCANNER_HIGH              | high       | activity      |    811
 Jboss Worm                    | JBOSS_WORM                        | medium     | worm          |    799
 NETBIOS Scanner               | NETBIOS_SCANNER_LOW               | low        | activity      |    799
 GoogleBot                     | GOOGLEBOT                         | high       | search_engine |    796
 PycURL HTTP Client            | PYCURL_HTTP_CLIENT                | high       | tool          |    760
 Censys                        | CENSYS                            | medium     | actor         |    736
 CPanel Scanner                | CPANEL_SCANNER_HIGH               | high       | activity      |    700
 IOT MQTT Scanner              | IOT_MQTT_SCANNER_LOW              | low        | activity      |    663
 Memcached Scanner             | MEMCACHED_SCANNER_HIGH            | high       | activity      |    625
 Elasticsearch Scanner         | ELASTICSEARCH_SCANNER_HIGH        | high       | activity      |    621
 Postgres Scanner              | POSTGRES_SCANNER_LOW              | low        | activity      |    576
 SNMP Scanner                  | SNMP_SCANNER_HIGH                 | high       | activity      |    549
 CPanel Scanner                | CPANEL_SCANNER_LOW                | low        | activity      |    542
 Dockerd Scanner               | DOCKERD_SCANNER_HIGH              | high       | activity      |    500
 BingBot                       | BINGBOT                           | high       | search_engine |    484
 Squid Proxy Scanner           | SQUID_PROXY_SCANNER_HIGH          | high       | activity      |    470
 Dockerd Scanner               | DOCKERD_SCANNER_LOW               | low        | activity      |    463
 NETBIOS Scanner               | NETBIOS_SCANNER_HIGH              | high       | activity      |    455
 Siemens PLC Scanner           | SIEMENS_PLC_SCANNER_LOW           | low        | activity      |    452
 Netis Router Admin Scanner    | NETIS_ROUTER_ADMIN_SCANNER_HIGH   | high       | activity      |    444
 SMTP Scanner                  | SMTP_SCANNER_HIGH                 | high       | activity      |    412
 LDAP Scanner                  | LDAP_SCANNER_LOW                  | low        | activity      |    412
 Netis Router Admin Scanner    | NETIS_ROUTER_ADMIN_SCANNER_LOW    | low        | activity      |    368
 SOCKS Proxy Scanner           | SOCKS_PROXY_SCANNER_HIGH          | high       | activity      |    359
 Siemens PLC Scanner           | SIEMENS_PLC_SCANNER_HIGH          | high       | activity      |    347
 Postgres Scanner              | POSTGRES_SCANNER_HIGH             | high       | activity      |    318
 PPTP VPN Scanner              | PPTP_VPN_SCANNER_LOW              | low        | activity      |    245
 Privoxy Proxy Scanner         | PRIVOXY_PROXY_SCANNER_LOW         | low        | activity      |    236
 IOT MQTT Scanner              | IOT_MQTT_SCANNER_HIGH             | high       | activity      |    228
 ShadowServer.org              | SHADOWSERVER                      | high       | actor         |    228
 Printer Scanner               | PRINTER_SCANNER_LOW               | low        | activity      |    225
 BinaryEdge.io                 | BINARYEDGE                        | high       | actor         |    221
 CGI Script Scanner            | CGI_SCRIPT_SCANNER                | low        | scanner       |    211
 RabbitMQ Scanner              | RABBITMQ_SCANNER_LOW              | low        | activity      |    210
 WinRM Scanner                 | WINRM_SCANNER_LOW                 | low        | activity      |    208
 IPSec VPN Scanner             | IPSEC_VPN_SCANNER_LOW             | low        | activity      |    207
 Minecraft Scanner             | MINECRAFT_SCANNER_LOW             | low        | activity      |    196
 Masscan Client                | MASSCAN_CLIENT                    | high       | tool          |    190
 TFTP Scanner                  | TFTP_SCANNER_LOW                  | low        | activity      |    170
 Privoxy Proxy Scanner         | PRIVOXY_PROXY_SCANNER_HIGH        | high       | activity      |    166
 LDAP Scanner                  | LDAP_SCANNER_HIGH                 | high       | activity      |    158
 Cassandra Scanner             | CASSANDRA_SCANNER_LOW             | low        | activity      |    157
 Ping Scanner                  | PING_SCANNER_LOW                  | high       | activity      |    151
 WinRM Scanner                 | WINRM_SCANNER_HIGH                | high       | activity      |    142
 ipip.net                      | IPIP                              | high       | actor         |    133
 Yandex Search Engine          | YANDEX_SEARCH_ENGINE              | high       | search_engine |    131
 D-Link 850L Worm              | DLINK_850L_WORM                   | high       | worm          |    128
 Baidu Spider                  | BAIDU_SPIDER                      | high       | search_engine |    117
 Bitcoin Node Scanner          | BITCOIN_NODE_SCANNER_LOW          | low        | activity      |    114
 Project Sonar                 | PROJECT_SONAR                     | high       | actor         |    114
 Printer Scanner               | PRINTER_SCANNER_HIGH              | high       | activity      |    109
 RabbitMQ Scanner              | RABBITMQ_SCANNER_HIGH             | high       | activity      |    108
 PPTP VPN Scanner              | PPTP_VPN_SCANNER_HIGH             | high       | activity      |    105
 TFTP Scanner                  | TFTP_SCANNER_HIGH                 | high       | activity      |    104
 Minecraft Scanner             | MINECRAFT_SCANNER_HIGH            | high       | activity      |     96
 NetCraft                      | NETCRAFT                          | high       | actor         |     93
 Python Requests Client        | PYTHON_REQUESTS_CLIENT            | high       | tool          |     89
 IPSec VPN Scanner             | IPSEC_VPN_SCANNER_HIGH            | high       | activity      |     66
 ZmEu Worm                     | ZMEU_WORM                         | high       | worm          |     59
 Shodan.io                     | SHODAN                            | high       | actor         |     52
 Fast HTTP Auth Scanner Client | FAST_HTTP_AUTH_SCANNER_CLIENT     | high       | tool          |     49
 Bitcoin Node Scanner          | BITCOIN_NODE_SCANNER_HIGH         | high       | activity      |     48
 Cobalt Strike Scanner         | COBALT_STRIKE_SCANNER_LOW         | low        | activity      |     43
 Ethereum Node Scanner         | ETHEREUM_NODE_SCANNER_LOW         | low        | activity      |     42
 Elasticsearch Scanner         | ELASTICSEARCH_SCANNER             | low        | activity      |     36
 Cassandra Scanner             | CASSANDRA_SCANNER_HIGH            | high       | activity      |     32
 Java HTTP Client              | JAVA_HTTP_CLIENT                  | high       | tool          |     26
 PDRLabs.net                   | PDRLABS                           | high       | actor         |     25
 Ethereum Node Scanner         | ETHEREUM_NODE_SCANNER_HIGH        | high       | activity      |     21
 Quadmetrics.com               | QUADMETRICS                       | high       | actor         |     20
 Go HTTP Client                | GO_HTTP_CLIENT                    | high       | tool          |     17
 Cobalt Strike Scanner         | COBALT_STRIKE_SCANNER_HIGH        | high       | activity      |     13
 LiteCoin Node Scanner         | LITECOIN_NODE_SCANNER_LOW         | low        | activity      |     10
 Pingdom.com                   | PINGDOM                           | high       | actor         |      9
 WinRM Scanner                 | WinRM_SCANNER_LOW                 | low        | activity      |      5
 CyberGreen                    | CYBERGREEN                        | high       | actor         |      3
 Team Cymru                    | TEAM_CYMRU                        | high       | actor         |      3
 ProbeTheNet.com               | PROBETHENET                       | high       | actor         |      3
 RWTH AACHEN University        | RWTH_AACHEN_UNIVERSITY            | high       | actor         |      3
 LiteCoin Node Scanner         | LITECOIN_NODE_SCANNER_HIGH        | high       | activity      |      3
 PingZapper                    | PINGZAPPER                        | high       | actor         |      2
 Ampere Innotech               | AMPERE_INNOTECH                   | high       | actor         |      2
 Cambridge Cybercrime Centre   | CAMBRIDGE_CYBERCRIME_CENTRE       | high       | actor         |      1
 Project25499                  | PROJECT25499                      | high       | actor         |      1
```
