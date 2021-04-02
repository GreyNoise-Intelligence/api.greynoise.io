# GreyNoise Public Community API

> :warning: **The GreyNoise Alpha (v1) API has been deprecated and replaced by the GreyNoise Community API.**

## Summary:

Cybersecurity teams are slammed. GreyNoise helps security analysts save time by revealing which events they can 
ignore. We do this by curating data on IPs that saturate security tools with noise. This unique perspective 
helps analysts confidently ignore irrelevant or harmless activity, creating more time to uncover and investigate true 
threats. 

The data is collected by a network of sensors deployed around the Internet in various datacenters, cloud providers, 
and regions.

## URL: 

```
https://api.greynoise.io/
```

## Endpoints:

* GET /v3/community/ip - query for information GreyNoise knows about a specific IP

### /v3/community/ip

Method: `GET`

- Required Parameters: NONE
- Optional Parameters: key

Example (unauthenticated):
```
$ curl -s 'https://api.greynoise.io/v3/community/8.8.8.8' | jq '.'
{
  "ip": "8.8.8.8",
  "noise": false,
  "riot": true,
  "classification": "benign",
  "name": "Google Public DNS",
  "link": "https://viz.greynoise.io/riot/8.8.8.8",
  "last_seen": "2021-03-26",
  "message": "Success"
}
```

Example (authenticated):
```
$ curl -s 'https://api.greynoise.io/v3/community/8.8.8.8' --header 'key: <api_key>' | jq '.'
{
  "ip": "1.1.1.1",
  "noise": false,
  "riot": true,
  "classification": "benign",
  "name": "Cloudflare Public DNS",
  "link": "https://viz.greynoise.io/riot/1.1.1.1",
  "last_seen": "2021-03-26",
  "message": "Success"
}
```


For more information, please visit:

- [Getting Started with the Community API](https://developer.greynoise.io/docs/using-the-greynoise-community-api)
- [API Reference - Community IP Lookup](https://developer.greynoise.io/reference/community-api#get_v3-community-ip)
