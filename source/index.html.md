---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Captain Data API! You can use our API to access Captain Data API endpoints, which can get information on various spiders and jobs in our database.

We have language bindings in Shell, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Authentication

> To authorize, you must add api_key to all request url:


```python
import requests

requests.get('https://api.skwid.io/v1/project_uid/spiders?key=api_key')
```

```shell
# With shell, you can just pass the correct header with each request
curl 'https://api.skwid.io/v1/project_uid/spiders?key=api_key'

```

```javascript
var http = new XMLHttpRequest();
xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
      spiders = this.response;
    }
  };
var url = 'https://api.skwid.io/v1/project_uid/spiders?key=api_key';
http.open('GET', url, true);
http.send();
```

> Make sure to replace `api_key` with your API key.

Captain Data uses API keys to allow access to the API.

Captain Data expects for the API key to be included in all API requests to the server in the url that looks like the following:

`https://api.skwid.io/v1/project_uid/spiders?key=api_key`

<aside class="notice">
You must replace <code>api_key</code> with your personal API key.
</aside>

# Spiders

## Get list of spiders for a specific project

```python
import requests

requests.get('https://api.skwid.io/v1/project_uid/spiders?key=api_key')
```

```shell
curl 'https://api.skwid.io/v1/project_uid/spiders?key=api_key'
```

```javascript
var http = new XMLHttpRequest();
xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
      spiders = this.response;
    }
  };
var url = 'https://api.skwid.io/v1/project_uid/spiders?key=api_key';
http.open('GET', url, true);
http.send();

```

> The above command returns JSON structured like this:

```json
[
  {"created_at": "Thu, 13 Sep 2018 13:45:51 GMT",
   "description": null,
   "jobs": null,
   "name": "Test Google",
   "permalink": "test-google",
   "schemas": [{"name": "Schema Bidon", "schema": {"name": null}}],
   "uid": "37307e83-d301-4b24-bd8f-6a39b6fe6fa0"
   },
  {"created_at": "Fri, 19 Oct 2018 10:20:48 GMT",
   "description": "Enrichment via pages jaunes - input SIRET",
   "jobs": null,
   "name": "Pages Jaunes SIRET",
   "permalink": "pages-jaunes-siret",
   "schemas": [{
   "name": "Company Enrich SIRET",
   "schema": {
      "address": null,
      "capital": null,
      "date": null,
      "directors": [],
      "domain": null,
      "legal_status": null,
      "naf_code": null,
      "name": null,
      "number_employees": null,
      "sales": null,
      "siren": null,
      "siret": null,
      "socials": {"fb": null, "in": null, "tw": null},
      "tel": null,
      "type": null
      }
   }],
   "uid": "8d5de183-3500-4b3c-9f7d-23b8955b44d3"
  }
]
```

This endpoint retrieves a list of spiders in JSON format.

### HTTP Request

`GET https://api.skwid.io/v1/project_uid/spiders?key=api_key`

### URL Parameters

Parameter | Description
--------- | -----------
project_uid `REQUIRED` | The uid of your project

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
key `REQUIRED` | null | Your client api_key
<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get last spider execution results

```python
import requests

requests.get('https://api.skwid.io/v1/project_uid/spiders/spider_uid/results/last?key=api_key')
```

```shell
curl 'https://api.skwid.io/v1/project_uid/spiders/spider_uid/results/last?key=api_key'
```

```javascript
var http = new XMLHttpRequest();
xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
      spiders = this.response;
    }
  };
var url = 'https://api.skwid.io/v1/project_uid/spiders/spider_uid/results/last?key=api_key';
http.open('GET', url, true);
http.send();
```

> The above command returns JSON structured like this:

```json
{ 
  "items_count": 12000,
  "limit": 1000,
  "pages": 12,
  "paging": {
    "next": "https://api.skwid.io/v1/project_uid/jobs/spider_uid/results?page=2&key=api_key", "previous": null},
  "results": [ 
    { 
      "_id": { "$oid": "5bccc821dee7b405b6253b18" },
      "address": [],
      "created_at": "2018-10-21T18:38:22.695837",
      "directors": [],
      "domain": null,
      "legal_status": [],
      "naf_code": [],
      "name": null,
      "number_employees": [],
      "siren": [],
      "siret": [],
      "socials": { "fb": null, "in": null, "tw": null },
      "source": "pages-jaunes",
      "status_complete": false,
      "tel": "01 75 77 13 77 ,01 75 77 13 77 ,01 75 77 13 77",
      "type": [],
      "url": "https://www.pagesjaunes.fr/pros/56111403"
    }, 
    { 
      "_id": { "$oid": "5bccc826dee7b405b6253b19" },
      "address": "90 bd Flandrin, 75116 PARIS 16",
      "captial": "300 K euros",
      "created_at": "2018-10-21T18:40:34.413729",
      "date": "12/11/2010",
      "directors": " Gérant : M Berger De La Villardiere Philippe",
      "domain": null,
      "legal_status": "Société à responsabilité limitée (sans autre indication)",
      "naf_code": "5829C",
      "name": "Fluxym",
      "number_employees": "0 salarié",
      "sales": "5 à 4 M euros",
      "siren": "444060974",
      "siret": "44406097400045",
      "socials": { "fb": null, "in": null, "tw": null },
      "source": "pages-jaunes",
      "tel": null,
      "tva": "FR66444060974",
      "type": "Siège",
      "url": "https://www.pagesjaunes.fr/siret/44406097400045" 
    }
    ...
  ]
}
```

This endpoint retrieves the items collection for a specific spider in JSON format.

### HTTP Request

`GET https://api.skwid.io/v1/project_uid/spiders?key=api_key`
### URL Parameters

Parameter | Description
--------- | -----------
project_uid `REQUIRED` | The uid of your project

### Query Parameters
Parameter | Default | Description |
--------- | ------- | ----------- |
key `REQUIRED` | null | Your client api_key |

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Schedule a spider

```python
import requests

body = {'start_urls': ['http://example.com']}
res = requests.post('https://api.skwid.io/v1/project_uid/spiders/spider_uid/schedule?key=api_key', json=body)
```

```shell
curl -X POST \
  'https://api.skwid.io/v1/c35bb2ce-e8b3-445c-b2b9-1ff6b6551ac2/spiders/8d5de183-3500-4b3c-9f7d-23b8955b44d3/schedule?key=api_key' \
  -H 'content-type: application/json' \
  -d '{
    "start_urls": []
  }'
```

```javascript
var data = JSON.stringify({
  "start_urls": ['http://example.com']
});

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://api.skwid.io/v1/project_uid/spiders/spider_uid/schedule?key=api_key");
xhr.setRequestHeader("content-type", "application/json");

xhr.send(data);
```

> The above command returns JSON structured like this:

```json
{
    "message": "Spider successfully scheduled.",
    "spider": {
        "created_at": "Tue, 11 Sep 2018 19:53:54 GMT",
        "description": null,
        "jobs": null,
        "name": "beta",
        "permalink": "beta",
        "schemas": [
            {
                "name": "rfferrr",
                "schema": {
                    "Name": "Hello World"
                }
            }
        ],
        "uid": "accce693-3dfa-48ee-b7b8-0656599d52ae"
    }
}
```

This endpoint schedules a spider by feeding it an (optional) list of start URLs.

### HTTP Request

`POST https://api.skwid.io/v1/project_uid/spiders/spider_uid/schedule?key=api_key`
### URL Parameters

Parameter | Description
--------- | -----------
project_uid `REQUIRED`| The uid of your project

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
key `REQUIRED`| null | Your client api_key
start_urls `REQUIRED`| null | List of start URLS

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Upload csv of start url for a spider

```python
import requests
files = {'csvFile': open(csv_path, 'rb')}
res = requests.post('https://api.skwid.io/v1/project_uid/spiders/spider_uid/upload?key=api_key', files=files)
```

```shell
curl -X POST
'http://127.0.0.1:5000/v1/project_uid/spiders/spider_uid/upload?key=api_key'
-H 'cache-control: no-cache'
-H 'content-type: multipart/form-data'
-F 'csvFile=@pathToCsv'
```

```javascript
var data = new FormData();
data.append("csvFile", csv_path);

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("POST", 'https://api.skwid.io/v1/project_uid/spiders/spider_uid/upload?key=api_key');
xhr.send(data);
```

> The above command returns JSON structured like this:

```json
{
    "message": "CSV uploaded.",
}
```

This endpoint upload csv of start url for a spider by feeding the CSV..

### HTTP Request

`POST https://api.skwid.io/v1/project_uid/spiders/spider_uid/upload?key=api_key`
### URL Parameters

Parameter | Description
--------- | -----------
project_uid `REQUIRED`| The uid of your project

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
key `REQUIRED`| null | Your client api_key
start_urls `REQUIRED` | null | List of start URLS

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

# Jobs
## Get list of jobs for a specific spider


```python
import requests

requests.get('https://api.skwid.io/v1/project_uid/spiders/spider_uid/jobs?key=api_key')
```

```shell
curl 'https://api.skwid.io/v1/project_uid/spiders/spider_uid/jobs?key=api_key'
```

```javascript
xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
      spiders = this.response;
    }
  };
var url = 'https://api.skwid.io/v1/project_uid/spiders/spider_uid/jobs?key=api_key';
http.open('GET', url, true);
http.send();
```

> The above command returns JSON structured like this:

```json
[
  {
     "downloader_request_count": 742,
     "downloader_response_count": 742,
     "finish_reason": null,
     "finish_time": {"$date": 1540167197906},
     "is_scheduled": false,
     "item_scraped_count": 147,
     "log_count_ERROR": null,
     "log_count_debug": 45035,
     "log_count_info": 13057,
     "memusage_max": 145813504,
     "memusage_startup": 72904704,
     "spider_permalink": "pages-jaunes-siret",
     "start_time": {"$date": 1540146981350},
     "status": "finished",
     "uid": "318826b4d56011e88540525400d49ff5"
  }, 
  {
     "downloader_request_count": 14,
     "downloader_response_count": 14,
     "finish_reason": null,
     "finish_time": {"$date": 1540144603755},
     "is_scheduled": false,
     "item_scraped_count": 4,
     "log_count_ERROR": null,
     "log_count_debug": 1785,
     "log_count_info": 498,
     "memusage_max": 78528512,
     "memusage_startup": 73023488,
     "spider_permalink": "pages-jaunes-siret",
     "start_time": {"$date": 1540144121356},
     "status": "finished",
     "uid": "89b1128ad55911e88540525400d49ff5"
  }
]
```

This endpoint retrieves a list of jobs for a specific spider in JSON format.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET https://api.skwid.io/v1/project_uid/spiders/spider_uid/jobs?key=api_key`

### URL Parameters

Parameter | Description
--------- | -----------
project_uid `REQUIRED`| The uid of your project
spider_uid `REQUIRED`| The uid of the spider 

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
key `REQUIRED`| null | Your client api_key

## Get specific job execution results

```python
import requests

requests.get('https://api.skwid.io/v1/project_uid/jobs/job_uid/results?key=api_key')
```

```shell
curl 'https://api.skwid.io/v1/project_uid/jobs/job_uid/results?key=api_key'
```

```javascript
xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
      spiders = this.response;
    }
  };
var url = 'https://api.skwid.io/v1/project_uid/jobs/job_uid/results?key=api_key';
http.open('GET', url, true);
http.send();
```

> The above command returns JSON structured like this:

```json

{ 
  "items_count": 147,
  "limit": 1000,
  "pages": 1,
  "paging": null,
  "results": [ 
    { 
      "_id": { "$oid": "5bccc821dee7b405b6253b18" },
      "address": [],
      "created_at": "2018-10-21T18:38:22.695837",
      "directors": [],
      "domain": null,
      "legal_status": [],
      "naf_code": [],
      "name": null,
      "number_employees": [],
      "siren": [],
      "siret": [],
      "socials": { "fb": null, "in": null, "tw": null },
      "source": "pages-jaunes",
      "status_complete": false,
      "tel": "01 75 77 13 77 ,01 75 77 13 77 ,01 75 77 13 77",
      "type": [],
      "url": "https://www.pagesjaunes.fr/pros/56111403"
    }, 
    { 
      "_id": { "$oid": "5bccc826dee7b405b6253b19" },
      "address": "90 bd Flandrin, 75116 PARIS 16",
      "captial": "300 K euros",
      "created_at": "2018-10-21T18:40:34.413729",
      "date": "12/11/2010",
      "directors": " Gérant : M Berger De La Villardiere Philippe",
      "domain": null,
      "legal_status": "Société à responsabilité limitée (sans autre indication)",
      "naf_code": "5829C",
      "name": "Fluxym",
      "number_employees": "0 salarié",
      "sales": "5 à 4 M euros",
      "siren": "444060974",
      "siret": "44406097400045",
      "socials": { "fb": null, "in": null, "tw": null },
      "source": "pages-jaunes",
      "tel": null,
      "tva": "FR66444060974",
      "type": "Siège",
      "url": "https://www.pagesjaunes.fr/siret/44406097400045" 
    }
    ...
  ]
}
```

This endpoint retrieves the items collection in JSON format.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET https://api.skwid.io/v1/project_uid/jobs/job_uid/results?key=api_key`

### URL Parameters

Parameter | Description
--------- | -----------
project_uid `REQUIRED`| The uid of your project
job_uid `REQUIRED`| The uid of the job 

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
key `REQUIRED`| null | Your client api_key
