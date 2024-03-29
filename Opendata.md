# Introduction


### API URL and protocol

The base URL for all API end-points is https://infoclient.api-atb.com/opendata.

All requests must use an HTTPS (SSL) connection.


### Authentication

The API requires all requests to include an Authorization header.

The API key is provided to you by the Aeroport Toulouse Blagnac.


### Rate limiting

Rate limiting is activated by default.

It depends on the usage plan agreed upon with ATB.


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


### Planned Arrivals

* Query string

    ```http
    https://infoclient.api-atb.com/opendata/planned/arrivals?page=1&limit=3&sortBy=dateheurevol&order=descending&start=2019-08-27&end=2019-08-28
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
    "total": 107,
    "count": 3,
    "results": [
        {
        "libelle": "AIRBUS A319",
        "hp": "00:40",
        "lig": "2549",
        "mvtnum": 1207199,
        "capacite": 140,
        "dateheurevol": "2019-08-28T22:40:00.000Z",
        "cie2l": "V7",
        "sens": "A",
        "datevol": "2019-08-29",
        "tags": [
            "arrivals"
        ],
        "esc1": "SPU",
        "cie1": "V7",
        "cie": "VOE",
        "timestamp": "2019-08-26T09:00:03.678Z"
        },
        {
        "libelle": "73H BOEING 737-800",
        "hp": "00:35",
        "lig": "1670",
        "mvtnum": 1234098,
        "capacite": 184,
        "eve": "AN",
        "dateheurevol": "2019-08-28T22:35:00.000Z",
        "cie2l": "AH",
        "sens": "A",
        "datevol": "2019-08-29",
        "tags": [
            "arrivals"
        ],
        "esc1": "ORN",
        "cie1": "AH",
        "cie": "DAH",
        "timestamp": "2019-08-26T09:00:11.545Z"
        },
        {
        "libelle": "E95 EMBRAER 195",
        "hp": "23:25",
        "lig": "494",
        "mvtnum": 895020,
        "capacite": 110,
        "dateheurevol": "2019-08-28T21:25:00.000Z",
        "cie2l": "TP",
        "sens": "A",
        "datevol": "2019-08-28",
        "tags": [
            "arrivals"
        ],
        "esc1": "LIS",
        "cie1": "TAP",
        "cie": "TAP",
        "timestamp": "2019-08-26T09:00:04.052Z"
        }
    ]
    }
    ````


### Planned Departures

* Query string

    ```http
    https://infoclient.api-atb.com/opendata/planned/departures?page=1&limit=3&sortBy=dateheurevol&order=descending&start=2019-08-27&end=2019-08-28
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
    "total": 88,
    "count": 3,
    "results": [
        {
        "nation": "I",
        "libelle": "73H BOEING 737-800",
        "hp": "01:35",
        "lig": "1671",
        "mvtnum": 1234099,
        "capacite": 184,
        "eve": "AN",
        "dateheurevol": "2019-08-28T23:35:00.000Z",
        "cie2l": "AH",
        "sens": "D",
        "datevol": "2019-08-29",
        "tags": [
            "departures"
        ],
        "esc1": "ORN",
        "cie1": "AH",
        "cie": "DAH",
        "timestamp": "2019-08-26T08:50:07.709Z"
        },
        {
        "nation": "I",
        "libelle": "73H BOEING 737-800",
        "hp": "23:05",
        "lig": "282",
        "mvtnum": 966996,
        "capacite": 184,
        "dateheurevol": "2019-08-28T21:05:00.000Z",
        "cie2l": "FR",
        "sens": "D",
        "datevol": "2019-08-28",
        "tags": [
            "departures"
        ],
        "esc1": "STN",
        "cie1": "FR",
        "cie": "RYR",
        "timestamp": "2019-08-26T08:50:02.472Z"
        },
        {
        "nation": "N",
        "libelle": "73H BOEING 737-800",
        "hp": "23:00",
        "lig": "1799",
        "mvtnum": 937776,
        "capacite": 184,
        "dateheurevol": "2019-08-28T21:00:00.000Z",
        "cie2l": "FR",
        "sens": "D",
        "datevol": "2019-08-28",
        "tags": [
            "departures"
        ],
        "esc1": "LIS",
        "cie1": "FR",
        "cie": "RYR",
        "timestamp": "2019-08-26T08:50:02.471Z"
        }
    ]
    }
    ````


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
    "total": 215,
    "count": 3,
    "results": [
        {
        "nation": "I",
        "hp": "00:40",
        "hall": "",
        "lig": "2549",
        "mvtnum": 1207199,
        "eta": "00:40",
        "capacite": "",
        "eve": "PR",
        "dateheurevol": "2019-08-28T22:40:00.000Z",
        "voltypeapp": "A319",
        "porte": "",
        "cie2l": "V7",
        "tapis": "7",
        "sens": "A",
        "datevol": "2019-08-29",
        "tags": [
            "arrivals_rt"
        ],
        "esc1": "SPU",
        "sortie": "04",
        "cie1": "V7",
        "cie": "VOE",
        "timestamp": "2019-08-28T10:42:20.373Z"
        },
        {
        "rem1_fr": "Annulé",
        "nation": "I",
        "hp": "00:35",
        "hall": "",
        "lig": "1670",
        "mvtnum": 1234098,
        "capacite": "",
        "eve": "AN",
        "dateheurevol": "2019-08-28T22:35:00.000Z",
        "voltypeapp": "B738",
        "porte": "",
        "rem_aff_en": "Cancelled",
        "cie2l": "AH",
        "sens": "A",
        "datevol": "2019-08-29",
        "rem1_en": "Cancelled",
        "tags": [
            "arrivals_rt"
        ],
        "esc1": "ORN",
        "rem_aff_fr": "Annulé",
        "cie1": "AH",
        "cie": "DAH",
        "timestamp": "2019-08-27T02:01:00.352Z"
        },
        {
        "nation": "N",
        "hp": "23:25",
        "hall": "",
        "lig": "494",
        "mvtnum": 895020,
        "eta": "23:08",
        "capacite": "",
        "eve": "PR",
        "dateheurevol": "2019-08-28T21:25:00.000Z",
        "voltypeapp": "E195",
        "porte": "",
        "cie2l": "TP",
        "tapis": "2",
        "sens": "A",
        "datevol": "2019-08-28",
        "tags": [
            "arrivals_rt"
        ],
        "esc1": "LIS",
        "sortie": "02",
        "cie1": "TP",
        "cie": "TAP",
        "timestamp": "2019-08-28T09:13:20.312Z"
        }
    ]
    }
    ````


### Realtime Departures

* Query string

    ```http
    https://infoclient.api-atb.com/opendata/realtime/departures?page=1&limit=3&sortBy=dateheurevol&order=descending&start=2019-08-27&end=2019-08-28
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
    "total": 215,
    "count": 3,
    "results": [
        {
        "nation": "I",
        "hp": "01:35",
        "lig": "1671",
        "mvtnum": 1234099,
        "dateheurevol": "2019-08-28T23:35:00.000Z",
        "sens": "D",
        "tags": [
            "departures_rt"
        ],
        "cie": "DAH",
        "rem1_fr": "Annulé",
        "capacite": "",
        "eve": "AN",
        "voltypeapp": "B738",
        "rem_aff_en": "Cancelled",
        "cie2l": "AH",
        "datevol": "2019-08-29",
        "rem1_en": "Cancelled",
        "esc1": "ORN",
        "rem_aff_fr": "Annulé",
        "cie1": "AH",
        "timestamp": "2019-08-27T03:01:20.348Z"
        },
        {
        "nation": "I",
        "hp": "23:05",
        "rem2_en": "Gate displayed at  21:25",
        "hall": "D14",
        "lig": "282",
        "mvtnum": 966996,
        "etd": "23:05",
        "dateheurevol": "2019-08-28T21:05:00.000Z",
        "sens": "D",
        "tags": [
            "departures_rt"
        ],
        "cie": "RYR",
        "capacite": "",
        "eve": "PR",
        "voltypeapp": "B738",
        "porte": "",
        "cie2l": "FR",
        "datevol": "2019-08-28",
        "rem2_fr": "Affichage porte à 21:25",
        "esc1": "STN",
        "cie1": "FR",
        "timestamp": "2019-08-28T09:18:20.261Z"
        },
        {
        "nation": "N",
        "hp": "23:00",
        "rem2_en": "Gate displayed at  22:15",
        "hall": "D12",
        "lig": "1799",
        "mvtnum": 937776,
        "etd": "23:00",
        "dateheurevol": "2019-08-28T21:00:00.000Z",
        "sens": "D",
        "tags": [
            "departures_rt"
        ],
        "cie": "RYR",
        "capacite": "",
        "eve": "PR",
        "voltypeapp": "B738",
        "porte": "",
        "cie2l": "FR",
        "datevol": "2019-08-28",
        "rem2_fr": "Affichage porte à 22:15",
        "esc1": "LIS",
        "cie1": "FR",
        "timestamp": "2019-08-28T09:13:20.115Z"
        }
    ]
    }
    ````


### Airports

* Query string

    ```http
    https://infoclient.api-atb.com/opendata/airports
    ```

* Parameters

    Nothing

* Response (200)

    Body

    ```json
    {
    "total": 103,
    "count": 103,
    "results": [
        {
        "code": "AGA",
        "libelle1": "Agadir",
        "libelle1_en": "Agadir",
        "tags": [
            "airports"
        ],
        "timestamp": "2019-08-26T08:44:20.661Z"
        },
        {
        "code": "BES",
        "libelle1": "Brest",
        "libelle1_en": "Brest",
        "tags": [
            "airports"
        ],
        "timestamp": "2019-08-26T08:44:20.671Z"
        },
        {
        "code": "BRE",
        "libelle1": "Brême",
        "libelle1_en": "Bremen",
        "tags": [
            "airports"
        ],
        "timestamp": "2019-08-26T08:44:20.671Z"
        }
    ]
    }
    ````


### Airlines

* Query string

    ```http
    https://infoclient.api-atb.com/opendata/airlines
    ```

* Parameters

    Nothing

* Response (200)

    Body

    ```json
    {
    "total": 76,
    "count": 76,
    "results": [
        {
        "libelle": "RYAN AIR",
        "cie2l": "FR",
        "cie": "RYR",
        "tags": [
            "airlines"
        ],
        "timestamp": "2019-08-26T08:44:20.681Z"
        },
        {
        "libelle": "SUN-AIR",
        "cie2l": "EZ",
        "cie": "SUS",
        "tags": [
            "airlines"
        ],
        "timestamp": "2019-08-26T08:44:20.682Z"
        },
        {
        "libelle": "ENTERAIR",
        "cie2l": "OF",
        "cie": "ENT",
        "tags": [
            "airlines"
        ],
        "timestamp": "2019-08-26T08:44:20.664Z"
        },
    ]
    }
    ````


### Waitingtimes

* Query string

    ```http
    https://infoclient.api-atb.com/opendata/waiting-times
    ```

* Parameters

    Nothing

* Response (200)

    Body

    ```json
    {
    "total": 3,
    "count": 3,
    "results": [
        {
        "waitingtimemax": -1,
        "waitingtimemin": -1,
        "waitingtime_aff": "2",
        "waitingtime": 2,
        "ecran": "PB_CTL",
        "tags": [
            "waiting_time"
        ],
        "timestamp": "2019-08-26T08:44:20.636Z"
        },
        {
        "waitingtimemax": -1,
        "waitingtimemin": -1,
        "waitingtime_aff": "2",
        "waitingtime": 2,
        "ecran": "PD_CTL",
        "tags": [
            "waiting_time"
        ],
        "timestamp": "2019-08-28T11:15:20.222Z"
        },
        {
        "waitingtime_aff": "5",
        "waitingtime": 4,
        "ecran": "Départs DPAF",
        "tags": [
            "waiting_time"
        ],
        "timestamp": "2019-08-28T11:17:20.124Z"
        }
    ]
    }
    ````


### Health

* Query string

    ```http
    https://infoclient.api-atb.com/opendata/health
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
        "secondsSinceLastUpdate": 19
        },
        {
        "name": "/realtime/departures",
        "status": "green",
        "secondsSinceLastUpdate": 19
        },
        {
        "name": "/planned/arrivals",
        "status": "green",
        "secondsSinceLastUpdate": 46892
        },
        {
        "name": "/planned/departures",
        "status": "green",
        "secondsSinceLastUpdate": 47492
        },
        {
        "name": "airports",
        "status": "green",
        "secondsSinceLastUpdate": 134459
        },
        {
        "name": "airlines",
        "status": "green",
        "secondsSinceLastUpdate": 182239
        },
        {
        "name": "/waiting-times",
        "status": "green",
        "secondsSinceLastUpdate": 79
        }
    ]
    }
    ````

***
