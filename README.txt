GreyNoise Intelligence Alpha API

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
