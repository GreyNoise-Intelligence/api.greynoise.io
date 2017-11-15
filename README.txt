GreyNoise Intelligence Alpha API

Summary:

Grey Noise is a system that collects and analyzes data on Internet-wide scanners. Grey Noise collects data on benign scanners such as Shodan.io, as well as malicious actors like SSH and telnet worms. 

The data is collected by a network of sensors deployed around the Internet in various datacenters, cloud providers, and regions.

The following is a snapshot of the data:

              tag_id               |   category    | confidence | count
-----------------------------------+---------------+------------+--------
 TELNET_SCANNER_LOW                | activity      | low        | 263949
 SMB_SCANNER_LOW                   | activity      | low        | 257344
 TELNET_WORM_HIGH                  | worm          | high       | 198050
 RESIDENTIAL                       | hosting       | high       | 161123
 TELNET_SCANNER_HIGH               | activity      | high       |  95534
 SMB_SCANNER_HIGH                  | activity      | high       |  90200
 WEB_SCANNER_LOW                   | activity      | low        |  77090
 MIRAI                             | worm          | high       |  74592
 SSH_SCANNER_LOW                   | activity      | low        |  47325
 SSH_WORM_HIGH                     | worm          | high       |  29422
 SSH_SCANNER_HIGH                  | activity      | high       |  15914
 HTTP_ALT_SCANNER_LOW              | activity      | low        |  13534
 MSSQL_SCANNER_LOW                 | activity      | low        |  10049
 PING_SCANNER_LOW                  | activity      | low        |   8340
 TELNET_WORM_LOW                   | worm          | low        |   7861
 MSSQL_SCANNER_HIGH                | activity      | high       |   7271
 RDP_SCANNER_LOW                   | activity      | low        |   5537
 WEB_SCANNER_HIGH                  | activity      | high       |   5131
 FTP_SCANNER_LOW                   | activity      | low        |   4713
 MYSQL_SCANNER_LOW                 | activity      | low        |   3657
 MYSQL_SCANNER_HIGH                | activity      | high       |   2995
 RDP_SCANNER_HIGH                  | activity      | high       |   2854
 HTTP_ALT_SCANNER_HIGH             | activity      | high       |   2535
 PING_SCANNER_HIGH                 | activity      | high       |   2093
 SMTP_SCANNER_LOW                  | activity      | low        |   1982
 PHPMYADMIN_WORM                   | worm          | high       |   1740
 DNS_SCANNER_LOW                   | activity      | low        |   1613
 SSH_WORM_LOW                      | worm          | low        |   1613
 SSDP_UPNP_SCANNER_LOW             | activity      | low        |   1253
 NTP_SCANNER_LOW                   | activity      | low        |   1202
 STRETCHOID                        | actor         | high       |   1187
 OPEN_PROXY_SCANNER                | activity      | high       |    955
 SSDP_UPNP_SCANNER_HIGH            | activity      | high       |    951
 VOIP_SCANNER_HIGH                 | activity      | high       |    922
 SQUID_PROXY_SCANNER_LOW           | activity      | low        |    859
 FTP_SCANNER_HIGH                  | activity      | high       |    727
 REDIS_SCANNER_LOW                 | activity      | low        |    721
 VNC_SCANNER_LOW                   | activity      | low        |    698
 ROUTER_RPC_SCANNER_LOW            | activity      | low        |    643
 VOIP_SCANNER_LOW                  | activity      | low        |    626
 VNC_SCANNER_HIGH                  | activity      | high       |    613
 SOCKS_PROXY_SCANNER_LOW           | activity      | low        |    591
 NTP_SCANNER_HIGH                  | activity      | high       |    568
 DNS_SCANNER_HIGH                  | activity      | high       |    530
 EMBEDDED_DEVICE_WORM              | worm          | high       |    527
 COUNTERSTRIKE_SERVER_SCANNER_LOW  | activity      | low        |    504
 MONGODB_SCANNER_LOW               | activity      | low        |    501
 REDIS_SCANNER_HIGH                | activity      | high       |    499
 JORGEE_HTTP_SCANNER               | tool          | high       |    482
 TOR                               | hosting       | high       |    476
 JBOSS_WORM                        | worm          | medium     |    446
 COUNTERSTRIKE_SERVER_SCANNER_HIGH | activity      | high       |    438
 MONGODB_SCANNER_HIGH              | activity      | high       |    432
 SNMP_SCANNER_LOW                  | activity      | low        |    392
 MEMCACHED_SCANNER_LOW             | activity      | low        |    383
 ROUTER_RPC_SCANNER_HIGH           | activity      | high       |    367
 UNKNOWN_LINUX_WORM                | worm          | high       |    354
 DOCKERD_SCANNER_HIGH              | activity      | high       |    351
 ELASTICSEARCH_SCANNER_LOW         | activity      | low        |    330
 CPANEL_SCANNER_HIGH               | activity      | high       |    320
 MEMCACHED_SCANNER_HIGH            | activity      | high       |    317
 CPANEL_SCANNER_LOW                | activity      | low        |    294
 DOCKERD_SCANNER_LOW               | activity      | low        |    292
 IOT_MQTT_SCANNER_LOW              | activity      | low        |    281
 CENSYS                            | actor         | medium     |    281
 SNMP_SCANNER_HIGH                 | activity      | high       |    275
 ELASTICSEARCH_SCANNER_HIGH        | activity      | high       |    266
 POSTGRES_SCANNER_LOW              | activity      | low        |    258
 SHADOWSERVER                      | actor         | high       |    228
 SQUID_PROXY_SCANNER_HIGH          | activity      | high       |    223
 GOOGLE_CLOUD                      | hosting       | high       |    221
 NETIS_ROUTER_ADMIN_SCANNER_HIGH   | activity      | high       |    200
 SOCKS_PROXY_SCANNER_HIGH          | activity      | high       |    183
 SIEMENS_PLC_SCANNER_LOW           | activity      | low        |    174
 PRIVOXY_PROXY_SCANNER_LOW         | activity      | low        |    169
 POSTGRES_SCANNER_HIGH             | activity      | high       |    161
 NETIS_ROUTER_ADMIN_SCANNER_LOW    | activity      | low        |    156
 WORDPRESS_WORM                    | worm          | medium     |    156
 SIEMENS_PLC_SCANNER_HIGH          | activity      | high       |    156
 PING_SCANNER_LOW                  | activity      | high       |    151
 GOOGLEBOT                         | search_engine | high       |    119
 IOT_MQTT_SCANNER_HIGH             | activity      | high       |    116
 MINECRAFT_SCANNER_LOW             | activity      | low        |    116
 CGI_SCRIPT_SCANNER                | scanner       | low        |    113
 PRINTER_SCANNER_LOW               | activity      | low        |    111
 RABBITMQ_SCANNER_LOW              | activity      | low        |    110
 TFTP_SCANNER_LOW                  | activity      | low        |     90
 WINRM_SCANNER_LOW                 | activity      | low        |     80
 PRIVOXY_PROXY_SCANNER_HIGH        | activity      | high       |     77
 BAIDU_SPIDER                      | search_engine | high       |     60
 CASSANDRA_SCANNER_LOW             | activity      | low        |     60
 IPIP                              | actor         | high       |     58
 RABBITMQ_SCANNER_HIGH             | activity      | high       |     58
 YANDEX_SEARCH_ENGINE              | search_engine | high       |     57
 WINRM_SCANNER_HIGH                | activity      | high       |     55
 MINECRAFT_SCANNER_HIGH            | activity      | high       |     53
 MASSCAN_CLIENT                    | tool          | high       |     52
 PRINTER_SCANNER_HIGH              | activity      | high       |     51
 TFTP_SCANNER_HIGH                 | activity      | high       |     51
 BITCOIN_NODE_SCANNER_LOW          | activity      | low        |     41
 ZMAP_CLIENT                       | tool          | high       |     41
 ELASTICSEARCH_SCANNER             | activity      | low        |     36
 BINARYEDGE                        | actor         | high       |     33
 PROJECT_SONAR                     | actor         | high       |     28
 PYCURL_HTTP_CLIENT                | tool          | high       |     26
 SHODAN                            | actor         | high       |     26
 COBALT_STRIKE_SCANNER_LOW         | activity      | low        |     22
 PYTHON_REQUESTS_CLIENT            | tool          | high       |     20
 PDRLABS                           | actor         | high       |     20
 ETHEREUM_NODE_SCANNER_LOW         | activity      | low        |     19
 BITCOIN_NODE_SCANNER_HIGH         | activity      | high       |     13
 CASSANDRA_SCANNER_HIGH            | activity      | high       |     10
 PINGDOM                           | actor         | high       |      9
 ZMEU_WORM                         | worm          | high       |      8
 ETHEREUM_NODE_SCANNER_HIGH        | activity      | high       |      5
 WinRM_SCANNER_LOW                 | activity      | low        |      5
 COBALT_STRIKE_SCANNER_HIGH        | activity      | high       |      4
 JAVA_HTTP_CLIENT                  | tool          | high       |      4
 FAST_HTTP_AUTH_SCANNER_CLIENT     | tool          | high       |      3
 GO_HTTP_CLIENT                    | tool          | high       |      3
 SMTP_SCANNER_HIGH                 | activity      | high       |      2

URL: http://api.greynoise.io:8888/

Endpoints:

GET /v1/query/list - list all tags
POST /v1/query/tag - query all IPs that have a given tag
POST /v1/query/ip - query all tags associated with a given IP

-- /v1/query/list (GET)

Required Parameters: NONE

Example:

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

-- /v1/query/ip (POST)

Required Parameters:
    <ip>

Example:

$ curl -s -XPOST -d 'ip=198.20.69.74' 'http://api.greynoise.io:8888/v1/query/ip'
{
  "ip": "198.20.69.74",
  "status": "exists",
  "records": [
    {
      "name": "VOIP Scanner",
      "first_seen": "2017-09-27T15:20:20.253Z",
      "last_updated": "2017-09-27T08:38:28.416Z",
      "confidence": "low",
      "intention": "",
      "category": "activity"
    },
    {
      "name": "Elasticsearch Scanner",
      "first_seen": "2017-09-27T19:36:14.127Z",
      "last_updated": "2017-09-27T03:27:26.431Z",
      "confidence": "low",
      "intention": "",
      "category": "activity"
    }
}

-- /v1/query/tag (POST)

Required Parameters:
    <tag>

Example:

$ curl -s -XPOST -d 'tag=YANDEX_SEARCH_ENGINE' http://api.greynoise.io:8888/v1/query/tag | jq '.'
{
  "tag": "YANDEX_SEARCH_ENGINE",
  "status": "ok",
  "records": [
    {
      "ip": "5.255.250.2",
      "name": "Yandex Search Engine",
      "first_seen": "2017-09-28T23:17:30.167Z",
      "last_updated": "2017-09-27T03:27:46.235Z",
      "confidence": "high",
      "Intention": "benign",
      "category": "search_engine"
    },
    {
      "ip": "5.255.250.6",
      "name": "Yandex Search Engine",
      "first_seen": "2017-09-28T23:17:30.215Z",
      "last_updated": "2017-09-27T03:27:46.245Z",
      "confidence": "high",
      "Intention": "benign",
      "category": "search_engine"
    }
}
