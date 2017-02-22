# SOAP-sink built with Zeep

A small microservice to post data to a SOAP endpoint.
All entities must have a "_soapheaders" attribute.

[![Build Status](https://travis-ci.org/sesam-community/sesam-ntlm-adapter.svg?branch=master)](https://travis-ci.org/sesam-community/sesam-ntlm-adapter)

##### Example entity
```
{
  "_ts": 1486128503194780,
  "_previous": null,
  "_hash": "50d93095f6fb68e7517ea89e62c60af8",
  "_id": "29932",
  "_deleted": false,
  "_updated": 8,
  "_soapheaders": {
    "header": {
      [...]
    }
  },
  "Medarbeider": {
    [...]
  }
}
```
##### Example configuration:

```
{
  "_id": "soap-service",
  "type": "system:microservice",
  "docker": {
    "environment": {
      "method": "createMedarbeiderEntity",
      "url": "http://localhost:8088/MedarbeiderAdapterV1_1?WSDL",
      # optional values below
      "authentication": "basic",
      "username": "theUsername",
      "password": "thePassword",
      "timeout": 30,
      "cipher": ":ECDHE-RSA-AES128-SHA",
      "transit_decode": "false"
    },
    "image": "sesambuild/soap-zeep-sink:latest",
    "port": 5001
  }
}
```
