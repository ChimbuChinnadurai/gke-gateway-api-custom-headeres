# gke-gateway-api-custom-headeres

This repository contains sample kubernetes manifests to test the custom request headers feature via GKE gateway API.

## Deploy the mainfests

```
kubectl apply -f .
```

## Test the endpoints and replace the Gateway API IP address in the request

```shell
Chimbus-MBP:Desktop chimbu$ curl -H "Host: http-echo-no-custom-header.example.com" 35.208.246.221
{
  "path": "/",
  "headers": {
    "host": "http-echo-no-custom-header.example.com",
    "user-agent": "curl/8.1.2",
    "accept": "*/*",
    "x-forwarded-proto": "http",
    "via": "1.1 google",
    "x-forwarded-for": "92.40.111.56,35.208.246.221"
  },
  "method": "GET",
  "body": "",
  "fresh": false,
  "hostname": "http-echo-no-custom-header.example.com",
  "ip": "35.208.246.221",
  "ips": [
    "35.208.246.221"
  ],
  "protocol": "http",
  "query": {},
  "subdomains": [
    "http-echo-no-custom-header"
  ],
  "xhr": false,
  "os": {
    "hostname": "http-echo-no-custom-header-76cf75fcdf-psqqz"
  },
  "connection": {}
}
```

```shell
Chimbus-MBP:Desktop chimbu$ curl -H "Host: http-echo-custom-header.example.com" 35.208.246.221
{
  "path": "/",
  "headers": {
    "host": "http-echo-custom-header.example.com",
    "user-agent": "curl/8.1.2",
    "accept": "*/*",
    "x-forwarded-proto": "http",
    "via": "1.1 google",
    "x-forwarded-for": "92.40.111.56,35.208.246.221",
    "x-devops-feature": "enabled"
  },
  "method": "GET",
  "body": "",
  "fresh": false,
  "hostname": "http-echo-custom-header.example.com",
  "ip": "35.208.246.221",
  "ips": [
    "35.208.246.221"
  ],
  "protocol": "http",
  "query": {},
  "subdomains": [
    "http-echo-custom-header"
  ],
  "xhr": false,
  "os": {
    "hostname": "http-echo-custom-header-6c586b7559-9sqrp"
  },
  "connection": {}
}
```