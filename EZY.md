# Introduction


### API URL and protocol

The base URL for all API end-points is https://infoclient.api-atb.com/ezy.

All requests must use an HTTPS (SSL) connection.


### Authentication

The API requires all requests to include an Authorization header.

The API key is provided to you by the Aeroport Toulouse Blagnac.


### Rate limiting

Rate limiting is activated by default. It depends on the usage plan agreed upon with ATB.


### Headers

* Request headers

    | Name      | Description             |
    |-----------|-------------------------|
    | x-api-key | The authorization token |

* Response headers

    | Name           | Description                                                                                                                                               |
    |----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
    | content-length | The length of the returned content in bytes                                                                                                               |
    | content-type   | Responses will always return as application/json                                                                                                          |
    | status         | The HTTP status                                                                                                                                           |
    | date           | Response date                                                                                                                                             |
    | via            | It is used for tracking message forwards, avoiding request loops, and  identifying the protocol capabilities of senders along the  request/response chain |
    | x-cache        | Indicates whether the response has been cached or not                                                                                                     |


### HTTP code status replies

* Main HTTP code status replies used in this API.

    | HTTP Status Code | Message               | Description                                                              |
    |------------------|-----------------------|--------------------------------------------------------------------------|
    | 200              | OK                    | The request was successful                                               |
    | 400              | Bad Request           | The request could not be understood because of bad or missing parameters |
    | 403              | Forbidden             | Access denied                                                            |
    | 429              | Too Many Request      | Client has made too many requests in a given time. Rate limiting applies |
    | 500              | Internal Server Error | Other errors from server that make the request a failure                 |


### Error handling

When the API returns a status code indicating an error, it will also include a JSON describing the error.

For example:

```json
{
    "message": "Bad Request"
}
```


### Date and time

All dates are expressed in ISO-8601 format.

If no time information is given in a moment representation, the time is assumed to be 00:00:00 (midnight).

* Example:

    ```bash
    2017-07-28 = 2017-07-27T00:00:00Z.
    ```

* Examples of valid ISO-8601 strings that represents all the same moment:

    ```bash
    2017-07-28
    2017-07-27T22:00:00.000Z
    2017-07-27T22Z
    2017-07-27T17:00:00.00-05:00
    2017-W30-5T05:00+07
    20170728
    20170727T220000Z
    20170727T170000-0500
    2017W305T0500+0700
    ```


### URL parameters

Query strings must be url encoded.


### Terms and conditions

TBD


### Troubleshooting

If you're experiencing any issues or any other difficulties, please contact us.


# Reference


### Realtime Arrivals

* Query string

    ```http
    https://infoclient.api-atb.com/opendata/realtime/arrivals?page=1&limit=3&sortBy=dateheurevol&order=descending&start=2019-08-27&end=2019-08-28
    ```

* Parameters

    | Parameters | Effect                                                                                                                           | Type    |
    |:-----------|:---------------------------------------------------------------------------------------------------------------------------------|:--------|
    | page       | The page number of results to view <ul><li>Default: 1</li></ul>                                                                  | Integer |
    | limit      | The number of results per page (max: 300) <ul><li>Default: 100</li></ul>                                                         | Integer |
    | sortBy     | A reference by which the flights will be sorted <ul><li>Default: dateheurevol</li><li>Possible values:dateheurevol</li></ul>     | Enum    |
    | order      | Determine the ordering of returned results  <ul><li>Default: descending</li><li>Possible values: ascending, descending</li></ul> | Enum    |
    | start      | An ISO-8601 date where time may be included <ul><li>Example: 2017-07-28T09:00:00</li></ul>                                       | String  |
    | end        | An ISO-8601 date where time may be included <ul><li>Example: 2017-07-28T09:00:00</li></ul>                                       | String  |

* Response (200)

    Body

    ```json
    {
      "total": 6,
      "count": 3,
      "results": [
        {
          "rem1_fr": "Débarqué à 21:49",
          "nation": "I",
          "hp": "21:30",
          "rem2_en": "Delivery completed",
          "hall": "",
          "lig": "8339",
          "mvtnum": 897432,
          "eta": "21:17",
          "capacite": "",
          "eve": "AR",
          "dateheurevol": "2019-08-28T19:30:00.000Z",
          "voltypeapp": "A320",
          "porte": "",
          "rem_aff_en": "Arrived 21:19",
          "cie2l": "U2",
          "tapis": "7",
          "sens": "A",
          "datevol": "2019-08-28",
          "rem1_en": "Disembarked at 21:49",
          "rem2_fr": "Livraison terminée",
          "tags": [
            "arrivals_rt"
          ],
          "esc1": "LGW",
          "sortie": "04",
          "rem_aff_fr": "Arrivé 21:19",
          "cie1": "EZY",
          "cie": "EZY",
          "timestamp": "2019-08-28T19:50:20.047Z"
        },
        {
          "rem1_fr": "Débarqué à 20:30",
          "nation": "N",
          "hp": "19:55",
          "rem2_en": "Delivery completed",
          "hall": "",
          "lig": "1716",
          "mvtnum": 918152,
          "eta": "19:55",
          "capacite": "",
          "eve": "AR",
          "dateheurevol": "2019-08-28T17:55:00.000Z",
          "voltypeapp": "A319",
          "porte": "",
          "rem_aff_en": "Arrived 20:00",
          "cie2l": "DS",
          "tapis": "1",
          "sens": "A",
          "datevol": "2019-08-28",
          "rem1_en": "Disembarked at 20:30",
          "rem2_fr": "Livraison terminée",
          "tags": [
            "arrivals_rt"
          ],
          "esc1": "BSL",
          "sortie": "02",
          "rem_aff_fr": "Arrivé 20:00",
          "cie1": "DS",
          "cie": "EZY",
          "timestamp": "2019-08-28T18:31:20.182Z"
        },
        {
          "rem1_fr": "Débarqué à 16:39",
          "nation": "I",
          "hp": "16:20",
          "rem2_en": "Delivery completed",
          "hall": "",
          "lig": "6139",
          "mvtnum": 931460,
          "eta": "16:05",
          "capacite": "",
          "eve": "AR",
          "dateheurevol": "2019-08-28T14:20:00.000Z",
          "voltypeapp": "A319",
          "porte": "",
          "rem_aff_en": "Arrived 16:09",
          "cie2l": "U2",
          "tapis": "6",
          "sens": "A",
          "datevol": "2019-08-28",
          "rem1_en": "Disembarked at 16:39",
          "rem2_fr": "Livraison terminée",
          "tags": [
            "arrivals_rt"
          ],
          "esc1": "BRS",
          "sortie": "04",
          "rem_aff_fr": "Arrivé 16:09",
          "cie1": "EZY",
          "cie": "EZY",
          "timestamp": "2019-08-28T14:40:20.273Z"
        }
      ]
    }
    ````


### Realtime Departures

* Query string

    ```http
    https://infoclient.api-atb.com/ezy/realtime/departures?page=1&limit=3&sortBy=dateheurevol&order=descending&start=2019-08-27&end=2019-08-28
    ```

* Parameters

    | Parameters | Effect                                                                                                                           | Type    |
    |:-----------|:---------------------------------------------------------------------------------------------------------------------------------|:--------|
    | page       | The page number of results to view <ul><li>Default: 1</li></ul>                                                                  | Integer |
    | limit      | The number of results per page (max: 300) <ul><li>Default: 100</li></ul>                                                         | Integer |
    | sortBy     | A reference by which the flights will be sorted <ul><li>Default: dateheurevol</li><li>Possible values:dateheurevol</li></ul>     | Enum    |
    | order      | Determine the ordering of returned results  <ul><li>Default: descending</li><li>Possible values: ascending, descending</li></ul> | Enum    |
    | start      | An ISO-8601 date where time may be included <ul><li>Example: 2017-07-28T09:00:00</li></ul>                                       | String  |
    | end        | An ISO-8601 date where time may be included <ul><li>Example: 2017-07-28T09:00:00</li></ul>                                       | String  |

* Response (200)

    Body

    ```json
    {
      "total": 6,
      "count": 3,
      "results": [
        {
          "nation": "I",
          "hp": "21:55",
          "hall": "C22-C25",
          "rem3_fr": "Embarquement terminé",
          "lig": "8340",
          "mvtnum": 896071,
          "etd": "22:04",
          "dateheurevol": "2019-08-28T19:55:00.000Z",
          "sens": "D",
          "tags": [
            "departures_rt"
          ],
          "rem3_en": "Boarding closed",
          "cie": "EZY",
          "rem1_fr": "Décollé à 22:14",
          "capacite": "",
          "eve": "DE",
          "voltypeapp": "A320",
          "porte": "53",
          "rem_aff_en": "Taken off 22:14",
          "cie2l": "U2",
          "datevol": "2019-08-28",
          "rem1_en": "Taken off 22:14",
          "esc1": "LGW",
          "rem_aff_fr": "Décollé à 22:14",
          "cie1": "EZY",
          "timestamp": "2019-08-28T20:15:20.061Z"
        },
        {
          "nation": "N",
          "hp": "20:30",
          "hall": "C22-C24",
          "rem3_fr": "Embarquement terminé",
          "lig": "1715",
          "mvtnum": 918042,
          "etd": "20:30",
          "dateheurevol": "2019-08-28T18:30:00.000Z",
          "sens": "D",
          "tags": [
            "departures_rt"
          ],
          "rem3_en": "Boarding closed",
          "cie": "EZY",
          "rem1_fr": "Décollé à 20:42",
          "capacite": "",
          "eve": "DE",
          "voltypeapp": "A319",
          "porte": "09",
          "rem_aff_en": "Taken off 20:42",
          "cie2l": "DS",
          "datevol": "2019-08-28",
          "rem1_en": "Taken off 20:42",
          "esc1": "BSL",
          "rem_aff_fr": "Décollé à 20:42",
          "cie1": "DS",
          "timestamp": "2019-08-28T18:43:20.150Z"
        },
        {
          "nation": "I",
          "hp": "16:50",
          "hall": "C22-C25",
          "rem3_fr": "Embarquement terminé",
          "lig": "6140",
          "mvtnum": 897150,
          "etd": "16:50",
          "dateheurevol": "2019-08-28T14:50:00.000Z",
          "sens": "D",
          "tags": [
            "departures_rt"
          ],
          "rem3_en": "Boarding closed",
          "cie": "EZY",
          "rem1_fr": "Décollé à 17:00",
          "capacite": "",
          "eve": "DE",
          "voltypeapp": "A319",
          "porte": "55",
          "rem_aff_en": "Taken off 17:00",
          "cie2l": "U2",
          "datevol": "2019-08-28",
          "rem1_en": "Taken off 17:00",
          "esc1": "BRS",
          "rem_aff_fr": "Décollé à 17:00",
          "cie1": "EZY",
          "timestamp": "2019-08-28T15:01:20.029Z"
        }
      ]
    }
    ````


### Health

* Query string

    ```http
    https://infoclient.api-atb.com/ezy/health
    ```

* Parameters

    Nothing

* Response (200)

    Body

    ```json
    {
      "resources": [
        {
          "name": "/realtime/arrivals",
          "status": "green",
          "secondsSinceLastUpdate": 41
        },
        {
          "name": "/realtime/departures",
          "status": "green",
          "secondsSinceLastUpdate": 41
        }
      ]
    }
    ````

***
