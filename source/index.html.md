---
title: API Reference

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  - python: Python
  - json: JSON Response

toc_footers:
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for interacting with the unofficial APIs of Korean Chart Platforms
---

# Introduction

Though Korean music platforms don't have public APIs similar to the ones kept by Spotify or Youtube, there are still easily accessible endpoints to fetch any information you want from their databases. The endpoints listed here were obtained by intercepting requests made by the apps or websites of the platforms, and while this might seem shady or illegal I have read terms of service and privacy policy of the platforms and there's nothing inherently wrong/illegal about this.

I only wrote a language binding in Python for now. You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/slatedocs/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Melon


> Define these headers and params at the beginning of your Python code to make the other requests simpler. 
> The examples here will assume both are always being used.

```python
headers = {
  "Accept-Charset": "utf-8",
  "Accept-Encoding": "gzip, deflate",
  "Connection": "Keep-Alive",
  "Host": "m2.melon.com",
  "User-Agent": "AS40; Android 12; 6.7.8.1"
}

params = {
  "cpId": "AS40",
  "cpKey": "14LNC3" 
}
``` 

Melon does not require any sort of authentication to interact with their database.

I do recommend using the following headers and parameters to ensure requests don't fail a lot.

Header | Value
-------- | -------
|Accept-Charset|utf-8
|Accept-Encoding|gzip,deflate
|Connection|Keep-Alive
|Host|m2.melon.com
|User-Agent|AS40; Android 12; 6.7.8.1

Parameter | Value 
----- | -----
cpId | AS40
cpKey | 14LNC3

## Top 100

> Make the request like this:

```python
import requests
url = "https://m2.melon.com/m6/chart/ent/songChartList.json"
response = requests.get(url, headers=headers)
data = response.json()
```

This endpoint retrieves the songs in the current Top 100 Chart and their positions.

### HTTP Request

`GET https://m2.melon.com/m6/chart/ent/songChartList.json`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
appVer | None | Can be set to any version of the Melon app, but not a required parameter.


> Running the code above returns JSON structured like this (Change to JSON Response to read it):

```json
{
  "httpsDomain": "https://m2.melon.com",
  "response": {
    "RANKDAY": "2024.04.07",
    "RANKHOUR": "09:00",
    "STATUS": "0",
    "SONGLIST": [ {
        "SONGID": "37138469",
        "SONGNAME": "나는 아픈 건 딱 질색이니까",
        "ALBUMID": "11402655",
        "ALBUMNAME": "2",
        "ARTISTLIST": [
          {
            "ARTISTID": "2137482",
            "ARTISTNAME": "(여자)아이들"
          }
        ],
        "PLAYTIME": "162",
        "GENRELIST": [
          {
            "GENRECODE": "GN0200",
            "GENRENAME": "댄스"
          },
          {
            "GENRECODE": "GN2500",
            "GENRENAME": "아이돌"
          }
        ],
        "CURRANK": "1",
        "PASTRANK": "1",
        "RANKGAP": "0",
        "RANKTYPE": "NONE",
        "ISMV": false,
        "ISADULT": false,
        "ISFREE": false,
        "ISHITSONG": false,
        "ISHOLDBACK": false,
        "ISTITLESONG": false,
        "ISSERVICE": true,
        "ISTRACKZERO": false,
        "ALBUMIMG": "https://cdnimg.melon.co.kr/cm2/album/images/114/02/655/11402655_20240129121016_500.jpg?c78f36957ea2f748def29fe988f9518c/melon/resize/144/optimize/90",
        "ALBUMIMGPATH": "https://cdnimg.melon.co.kr/cm2/album/images/114/02/655/11402655_20240129121016_500.jpg?c78f36957ea2f748def29fe988f9518c/melon/resize/144/optimize/90",
        "ALBUMIMGLARGE": "https://cdnimg.melon.co.kr/cm2/album/images/114/02/655/11402655_20240129121016_500.jpg?c78f36957ea2f748def29fe988f9518c/melon/optimize/90",
        "ALBUMIMGSMALL": "https://cdnimg.melon.co.kr/cm2/album/images/114/02/655/11402655_20240129121016_500.jpg?c78f36957ea2f748def29fe988f9518c/melon/resize/50/optimize/90",
        "ISSUEDATE": "2024.01.29",
        "CTYPE": "1",
        "CONTSTYPECODE": "N10001"
      } 
      // Other 99 song elements with the same structure]
    ],
    "CHARTINFO": {
      "LINKURL": "https://m2.melon.com/m6/chart/chartEntInfo.htm?cpId=AS40&appVer=6.7.8.1",
      "LINKTYPE": "ZA"
    },
    "STATSELEMENTS": {
      "IMPRESSIONID": "",
      "RANGECODE": "1000002737"
    },
    "MENUID": "1000002721",
    "SECTION": "멜론차트",
    "PAGE": "멜론차트_TOP100NOW"
  }
  "httpDomain": "http://m2.melon.com"
}
```

## Hot 100

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```python
import K-Chart DAtabase

api = K-Chart DAtabase.authorize('meowmeowmeow')
api.kittens.delete(2)
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

