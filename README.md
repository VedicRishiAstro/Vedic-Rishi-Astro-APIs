##Vedic Rishi Astro APIs

Vedic Rishi does all the complex astronomical and algorithmic calculations for your astrology websites or astro-matching apps and provides you with simple APIs to create awesome user interfaces for your users

#### Vedic Rishi REST Web Service Interface

Since the Vedic Rishi Astro API is based on REST principles, it's very easy to write and test applications. You can use your browser to access URLs, and you can use pretty much any HTTP client in any programming language to interact with the API.

#### API Endpoint

All API URLs listed in this documentation are relative to **https://api.vedicrishiastro.com/v1**  
For example - the /horo_chart/D1/ API call is reachable at-  
<span class="text-info">https://api.vedicrishiastro.com/v1/horo_chart/D1/</span>

#### RESTful

All Vedic Rishi Astro APIs are RESTful APIs. Following are the known caveats -

1.  All API calls should be made with HTTP POST unless mentioned otherwise
2.  Response status other than HTTP 200 can be considered as an error
3.  Basic HTTP header authorization data is must for every API call

#### Passing Requested Data RESTfully

Request data is passed to the API by POSTing JSON objects to the API endpoints with the appropriate parameters. The documentation for each API call will contain more detail on the parameters accepted by the call. As an alternative, you can also use HTTP POST parameters, just like submitting an HTML FORM, but JSON objects are recommended.

#### Output Format

Response data for each and every Vedic Rishi Astro API will be encoded in JSON format.

#### Authentication

Vedic Rishi authenticates the API access using header authentication, therefore every API call to Vedic Rishi must have authorisation header set as- _Authorization: Basic ("userId:APIKey")_  
API key and userId will be mailed to you once you subscribe and activate your plan.

#### How to get latitude ,longitude and timezone ?

For all the astrological calculcations and other reports generation (Except Numerology), Vedic Rishi APIs expect birth details which contain date of birth, time of birth, longitude of birth place, latitude of birth place and timezone of birth country. We know that getting latitude, longitude and timezone of all the places are difficult to get and therefore Vedic Rishi solves this problem by providing FREE APIs for getting the geo-details given city. These APIs are included in each and every plan you subscribe from VedicRishi. [Know More..](/docs/api-ref/geodetails)

#### Official API Clients

We have an official github account which maintains the official API clients written in various languages.

[Vedic Rishi Astro API PHP Client](https://github.com/chandantiwari/Vedic-Rishi-Astro-API-PHP-Client)

##Advanced Panchang

This is the extension of basic panchang which provides various yog such as dwi-pushakar timing, tri-pushkar timing, sarvarth siddhi yog, amrit siddhi yog, ravi yog along with malefic yog such as rahu kal, yam-ghant kal and gulik kal.

#### We have two types of Panchang APIs

**1\. Panchang at specified date and time**
Here, following APIs are used and date and time along with latitude, longitude and timezone are expected -

*   [1\. basic_panchang](#-basic-panchang/basic_panchang)
*   [2\. planet_panchang](#-basic-panchang/planet_panchang)
*   [3\. advanced_panchang](#-advanced-panchang/advanced_panchang)

**2\. Panchang at Sunsrise for given day**
Following APIs should be used for getting the panchang data points at the time of sunrise which are used by traditional calendars-

*   [1\. basic_panchang/sunrise](#-basic-panchang/basic_panchang/sunrise)
*   [2\. planet_panchang/sunrise](#-basic-panchang/planet_panchang/sunrise)
*   [2\. advanced_panchang/sunrise](#-advanced-panchang/advanced_panchang/sunrise)
*   [4\. chaughadiya_muhurta](#-advanced-panchang/chaughadiya_muhurta)
*   [5\. hora_muhurta](#-advanced-panchang/hora_muhurta)

**" Here only date along with latitude, longitude and timezone are expected to be passed. No time is required. "**

### advanced_panchang

Provides panchang in details for given day at perticular given time.

#### API Endpoint

advanced_panchang

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/advanced_panchang |



#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Panchang day, eg: 10 |
| month     | int      |   Panchang month, eg:5 |
| year | int      |    Panchang year, eg:2015 |
| hour | int | Panchang hour, eg:12 |
| min | int | Panchang minute, eg:34 |
| lat | float | Panchang place latitude, eg: 19.234|
| lon | float | Panchang place longitude, eg: 72.843|
| tzone | float | Panchang place timezone, eg: 5.5|

#### Response Data ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```javascript
{
  "day": "Wednesday",
  "sunrise": "7:3:17",
  "sunset": "18:43:38",
  "moonrise": "10:59:45",
  "moonset": "0:9:13",
  "tithi": {
    "details": {
      "tithi_number": 7,
      "tithi_name": "Shukla-Saptami",
      "special": "Bhadra Tithi",
      "summary": "Favourable for starting any new work, debate, beginning of a journey and physical exercise.",
      "deity": "Indra"
    },
    "end_time": {
      "hour": 10,
      "minute": 55,
      "second": 8
    }
  },
  "nakshatra": {
    "details": {
      "nak_number": 3,
      "nak_name": "Krittika",
      "ruler": "Sun",
      "deity": "Agni",
      "special": "Adhomukh Nakshatra",
      "summary": "This nakshatra is of a mixed quality. Good for immediate actions, competition, work with metals. It is suitable to perform the routine activities, day-to-day duties, but it is not recommended to start new important deeds."
    },
    "end_time": {
      "hour": 17,
      "minute": 48,
      "second": 8
    }
  },
  "yog": {
    "details": {
      "yog_number": 26,
      "yog_name": "Endra",
      "special": "Auspicious yoga,Good for all Auspicious Deeds.",
      "meaning": "(Chief) � interest in education and knowledge; helpful, well-off."
    },
    "end_time": {
      "hour": 7,
      "minute": 57,
      "second": 19
    }
  },
  "karan": {
    "details": {
      "karan_number": 7,
      "karan_name": "Vanija",
      "special": "It is suited for sale transactions and sellers may reap good profits whereas buyers may incur losses in this Karana.",
      "deity": "Manibhadra"
    },
    "end_time": {
      "hour": 10,
      "minute": 57,
      "second": 8
    }
  },
  "hindu_maah": {
    "adhik_status": false,
    "purnimanta": "Phalguna",
    "amanta": "Phalguna"
  },
  "paksha": "Shukla-Paksha",
  "ritu": "Shishir",
  "sun_sign": "Aquarius",
  "moon_sign": "Taurus",
  "ayana": "Uttarayana",
  "panchang_yog": " Sarvarth Siddhi Yog",
  "vikram_samvat": 2071,
  "shaka_samvat": 1936,
  "shaka_samvat_name": "Jay",
  "vkram_samvat_name": "Plavang",
  "disha_shool": "NORTH",
  "disha_shool_remedies": [],
  "nak_shool": "none",
  "moon_nivas": "SOUTH",
  "abhijit_muhurta": {
    "start": "12:29",
    "end": "01:15"
  },
  "rahukaal": {
    "start": "12 : 52 : 59",
    "end": "2 : 20 : 29"
  },
  "guliKaal": {
    "start": "11 : 25 : 29",
    "end": "12 : 52 : 59"
  },
  "yamghant_kaal": {
    "start": "08 : 30 : 29",
    "end": "09 : 57 : 59"
  }
}

```

### advanced_panchang/sunrise

Provides panchang in details at the time of sunrise for given day.

#### API Endpoint

advanced_panchang/sunrise

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/advanced_panchang/sunrise |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Panchang day, eg: 10 |
| month     | int      |   Panchang month, eg:5 |
| year | int      |    Panchang year, eg:2015 |
| lat | float | Panchang place latitude, eg: 19.234|
| lon | float | Panchang place longitude, eg: 72.843|
| tzone | float | Panchang place timezone, eg: 5.5|

#### Response Data ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```javascript
{
  "day": "Wednesday",
  "sunrise": "7:3:17",
  "sunset": "18:43:38",
  "moonrise": "10:59:45",
  "moonset": "0:9:13",
  "tithi": {
    "details": {
      "tithi_number": 7,
      "tithi_name": "Shukla-Saptami",
      "special": "Bhadra Tithi",
      "summary": "Favourable for starting any new work, debate, beginning of a journey and physical exercise.",
      "deity": "Indra"
    },
    "end_time": {
      "hour": 10,
      "minute": 55,
      "second": 8
    }
  },
  "nakshatra": {
    "details": {
      "nak_number": 3,
      "nak_name": "Krittika",
      "ruler": "Sun",
      "deity": "Agni",
      "special": "Adhomukh Nakshatra",
      "summary": "This nakshatra is of a mixed quality. Good for immediate actions, competition, work with metals. It is suitable to perform the routine activities, day-to-day duties, but it is not recommended to start new important deeds."
    },
    "end_time": {
      "hour": 17,
      "minute": 48,
      "second": 8
    }
  },
  "yog": {
    "details": {
      "yog_number": 26,
      "yog_name": "Endra",
      "special": "Auspicious yoga,Good for all Auspicious Deeds.",
      "meaning": "(Chief) � interest in education and knowledge; helpful, well-off."
    },
    "end_time": {
      "hour": 7,
      "minute": 57,
      "second": 19
    }
  },
  "karan": {
    "details": {
      "karan_number": 7,
      "karan_name": "Vanija",
      "special": "It is suited for sale transactions and sellers may reap good profits whereas buyers may incur losses in this Karana.",
      "deity": "Manibhadra"
    },
    "end_time": {
      "hour": 10,
      "minute": 57,
      "second": 8
    }
  },
  "hindu_maah": {
    "adhik_status": false,
    "purnimanta": "Phalguna",
    "amanta": "Phalguna"
  },
  "paksha": "Shukla-Paksha",
  "ritu": "Shishir",
  "sun_sign": "Aquarius",
  "moon_sign": "Taurus",
  "ayana": "Uttarayana",
  "panchang_yog": " Sarvarth Siddhi Yog",
  "vikram_samvat": 2071,
  "shaka_samvat": 1936,
  "shaka_samvat_name": "Jay",
  "vkram_samvat_name": "Plavang",
  "disha_shool": "NORTH",
  "disha_shool_remedies": [],
  "nak_shool": "none",
  "moon_nivas": "SOUTH",
  "abhijit_muhurta": {
    "start": "12:29",
    "end": "01:15"
  },
  "rahukaal": {
    "start": "12 : 52 : 59",
    "end": "2 : 20 : 29"
  },
  "guliKaal": {
    "start": "11 : 25 : 29",
    "end": "12 : 52 : 59"
  },
  "yamghant_kaal": {
    "start": "08 : 30 : 29",
    "end": "09 : 57 : 59"
  }
}

```

### chaughadiya_muhurta

Provides both day and night chaughadiya data.

#### API Endpoint

chaughadiya_muhurta

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/chaughadiya_muhurta |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Panchang day, eg: 10 |
| month     | int      |   Panchang month, eg:5 |
| year | int      |    Panchang year, eg:2015 |
| lat | float | Panchang place latitude, eg: 19.234|
| lon | float | Panchang place longitude, eg: 72.843|
| tzone | float | Panchang place timezone, eg: 5.5|

#### Response Data ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```javascript
{
  "chaughadiya": {
    "day": [
      {
        "time": "5 : 41 : 01 - 4 : 06 : 50",
        "muhurta": "Labh"
      },
      {
        "time": "4 : 06 : 50 - 2 : 32 : 39",
        "muhurta": "Amrit"
      },
      {
        "time": "2 : 32 : 39 - 12 : 58 : 27",
        "muhurta": "Kaal"
      },
      {
        "time": "12 : 58 : 27 - 11 : 24 : 16",
        "muhurta": "Shubh"
      },
      {
        "time": "11 : 24 : 16 - 09 : 50 : 05",
        "muhurta": "Rog"
      },
      {
        "time": "09 : 50 : 05 - 08 : 15 : 53",
        "muhurta": "Udveg"
      },
      {
        "time": "08 : 15 : 53 - 06 : 41 : 42",
        "muhurta": "Char"
      },
      {
        "time": "06 : 41 : 42 - 05 : 07 : 30",
        "muhurta": "Labh"
      }
    ],
    "night": [
      {
        "time": "05 : 07 : 30 - 06 : 41 : 38",
        "muhurta": "Udveg"
      },
      {
        "time": "06 : 41 : 38 - 08 : 15 : 46",
        "muhurta": "Shubh"
      },
      {
        "time": "08 : 15 : 46 - 09 : 49 : 55",
        "muhurta": "Amrit"
      },
      {
        "time": "09 : 49 : 55 - 11 : 24 : 03",
        "muhurta": "Char"
      },
      {
        "time": "11 : 24 : 03 - 12 : 58 : 11",
        "muhurta": "Rog"
      },
      {
        "time": "12 : 58 : 11 - 2 : 32 : 19",
        "muhurta": "Kaal"
      },
      {
        "time": "2 : 32 : 19 - 4 : 06 : 27",
        "muhurta": "Labh"
      },
      {
        "time": "4 : 06 : 27 - 5 : 40 : 35",
        "muhurta": "Udveg"
      }
    ]
  }
}

```
### hora_muhurta

Provides day and night hora data.

#### API Endpoint

hora_muhurta

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/chaughadiya_muhurta |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Panchang day, eg: 10 |
| month     | int      |   Panchang month, eg:5 |
| year | int      |    Panchang year, eg:2015 |
| lat | float | Panchang place latitude, eg: 19.234|
| lon | float | Panchang place longitude, eg: 72.843|
| tzone | float | Panchang place timezone, eg: 5.5|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```javascript
{
  "hora": {
    "day": [
      {
        "time": "17:41 - 18:41",
        "hora": "Mercury"
      },
      {
        "time": "18:41 - 19:41",
        "hora": "Moon"
      },
      {
        "time": "19:41 - 20:41",
        "hora": "Saturn"
      },
      {
        "time": "20:41 - 21:41",
        "hora": "Jupiter"
      },
      {
        "time": "21:41 - 22:41",
        "hora": "Mars"
      },
      {
        "time": "22:41 - 23:41",
        "hora": "Sun"
      },
      {
        "time": "23:41 - 0:41",
        "hora": "Venus"
      },
      {
        "time": "0:41 - 1:41",
        "hora": "Mercury"
      },
      {
        "time": "1:41 - 2:41",
        "hora": "Moon"
      },
      {
        "time": "2:41 - 3:41",
        "hora": "Saturn"
      },
      {
        "time": "3:41 - 4:41",
        "hora": "Jupiter"
      },
      {
        "time": "4:41 - 5:41",
        "hora": "Mars"
      }
    ],
    "night": [
      {
        "time": "5:41 - 6:41",
        "hora": "Sun"
      },
      {
        "time": "6:41 - 7:41",
        "hora": "Venus"
      },
      {
        "time": "7:41 - 8:41",
        "hora": "Mercury"
      },
      {
        "time": "8:41 - 9:41",
        "hora": "Moon"
      },
      {
        "time": "9:41 - 10:41",
        "hora": "Saturn"
      },
      {
        "time": "10:41 - 11:41",
        "hora": "Jupiter"
      },
      {
        "time": "11:41 - 12:41",
        "hora": "Mars"
      },
      {
        "time": "12:41 - 13:41",
        "hora": "Sun"
      },
      {
        "time": "13:41 - 14:41",
        "hora": "Venus"
      },
      {
        "time": "14:41 - 15:41",
        "hora": "Mercury"
      },
      {
        "time": "15:41 - 16:41",
        "hora": "Moon"
      },
      {
        "time": "16:41 - 17:41",
        "hora": "Saturn"
      }
    ]
  }
}

```

## Basic Ashtakvarga

Provide details of Bhinnashtak varga And Servashtak Varga.

### planet_ashtak/:planet_name

Provides astakvarga chart points and table points.

#### API Endpoint
planet_ashtak/:planet_name

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/planet_ashtak/:planet_name |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Panchang day, eg: 10 |
| month     | int      |   Panchang month, eg:5 |
| year | int      |    Panchang year, eg:2015 |
| lat | float | Panchang place latitude, eg: 19.234|
| lon | float | Panchang place longitude, eg: 72.843|
| tzone | float | Panchang place timezone, eg: 5.5|

#### Planet Name
Here planet name means for which planet you want data.
>Planet name's are as follow:- 
>sun, moon, mars, mercury, jupiter, venus, saturn , ascendant

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")

``` javascript
{
  "ashtak_varga": {
    "type": "Bhinnashtak",
    "planet": "Sun",
    "sign": "virgo",
    "sign_id": 6
  },
  "ashtak_points": {
    "aries": {
      "sun": 0,
      "moon": 0,
      "mars": 1,
      "mercury": 0,
      "jupiter": 0,
      "venus": 0,
      "saturn": 0,
      "ascendant": 0,
      "total": 1
    },
    "taurus": {
      "sun": 1,
      "moon": 1,
      "mars": 0,
      "mercury": 1,
      "jupiter": 1,
      "venus": 0,
      "saturn": 1,
      "ascendant": 1,
      "total": 6
    },
    "gemini": {
      "sun": 0,
      "moon": 0,
      "mars": 1,
      "mercury": 1,
      "jupiter": 0,
      "venus": 0,
      "saturn": 1,
      "ascendant": 1,
      "total": 4
    },
    "cancer": {
      "sun": 0,
      "moon": 0,
      "mars": 0,
      "mercury": 0,
      "jupiter": 0,
      "venus": 0,
      "saturn": 1,
      "ascendant": 1,
      "total": 2
    },
    "leo": {
      "sun": 1,
      "moon": 1,
      "mars": 0,
      "mercury": 0,
      "jupiter": 0,
      "venus": 1,
      "saturn": 1,
      "ascendant": 0,
      "total": 4
    },
    "virgo": {
      "sun": 1,
      "moon": 0,
      "mars": 1,
      "mercury": 1,
      "jupiter": 0,
      "venus": 1,
      "saturn": 1,
      "ascendant": 0,
      "total": 5
    },
    "libra": {
      "sun": 1,
      "moon": 0,
      "mars": 1,
      "mercury": 1,
      "jupiter": 0,
      "venus": 0,
      "saturn": 0,
      "ascendant": 1,
      "total": 4
    },
    "scorpio": {
      "sun": 1,
      "moon": 0,
      "mars": 1,
      "mercury": 1,
      "jupiter": 1,
      "venus": 0,
      "saturn": 1,
      "ascendant": 1,
      "total": 6
    },
    "sagittarius": {
      "sun": 1,
      "moon": 1,
      "mars": 1,
      "mercury": 1,
      "jupiter": 1,
      "venus": 0,
      "saturn": 1,
      "ascendant": 0,
      "total": 6
    },
    "capricorn": {
      "sun": 0,
      "moon": 1,
      "mars": 1,
      "mercury": 0,
      "jupiter": 0,
      "venus": 0,
      "saturn": 0,
      "ascendant": 1,
      "total": 3
    },
    "aquarius": {
      "sun": 1,
      "moon": 0,
      "mars": 0,
      "mercury": 0,
      "jupiter": 0,
      "venus": 1,
      "saturn": 1,
      "ascendant": 0,
      "total": 3
    },
    "pisces": {
      "sun": 1,
      "moon": 0,
      "mars": 1,
      "mercury": 1,
      "jupiter": 1,
      "venus": 0,
      "saturn": 0,
      "ascendant": 0,
      "total": 4
    }
  }
}

```

### sarvashtak

Provides sarvashtak varga chart points and table points.

#### API Endpoint
sarvashtak

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/sarvashtak |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Panchang day, eg: 10 |
| month     | int      |   Panchang month, eg:5 |
| year | int      |    Panchang year, eg:2015 |
| lat | float | Panchang place latitude, eg: 19.234|
| lon | float | Panchang place longitude, eg: 72.843|
| tzone | float | Panchang place timezone, eg: 5.5|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")

``` javascript
{
  "ashtak_varga": {
    "type": "Sarvashtak"
  },
  "ashtak_points": {
    "aries": {
      "sun": 1,
      "moon": 5,
      "mars": 3,
      "mercury": 3,
      "jupiter": 8,
      "venus": 4,
      "saturn": 1,
      "ascendant": 0,
      "total": 25
    },
    "taurus": {
      "sun": 6,
      "moon": 6,
      "mars": 5,
      "mercury": 5,
      "jupiter": 4,
      "venus": 5,
      "saturn": 5,
      "ascendant": 0,
      "total": 36
    },
    "gemini": {
      "sun": 4,
      "moon": 3,
      "mars": 6,
      "mercury": 8,
      "jupiter": 3,
      "venus": 5,
      "saturn": 3,
      "ascendant": 0,
      "total": 32
    },
    "cancer": {
      "sun": 2,
      "moon": 5,
      "mars": 2,
      "mercury": 3,
      "jupiter": 3,
      "venus": 4,
      "saturn": 1,
      "ascendant": 0,
      "total": 20
    },
    "leo": {
      "sun": 4,
      "moon": 4,
      "mars": 4,
      "mercury": 3,
      "jupiter": 4,
      "venus": 3,
      "saturn": 6,
      "ascendant": 0,
      "total": 28
    },
    "virgo": {
      "sun": 5,
      "moon": 4,
      "mars": 2,
      "mercury": 4,
      "jupiter": 6,
      "venus": 4,
      "saturn": 3,
      "ascendant": 0,
      "total": 28
    },
    "libra": {
      "sun": 4,
      "moon": 3,
      "mars": 3,
      "mercury": 5,
      "jupiter": 5,
      "venus": 3,
      "saturn": 2,
      "ascendant": 0,
      "total": 25
    },
    "scorpio": {
      "sun": 6,
      "moon": 4,
      "mars": 3,
      "mercury": 5,
      "jupiter": 5,
      "venus": 6,
      "saturn": 4,
      "ascendant": 0,
      "total": 33
    },
    "sagittarius": {
      "sun": 6,
      "moon": 4,
      "mars": 3,
      "mercury": 6,
      "jupiter": 4,
      "venus": 3,
      "saturn": 4,
      "ascendant": 0,
      "total": 30
    },
    "capricorn": {
      "sun": 3,
      "moon": 7,
      "mars": 4,
      "mercury": 6,
      "jupiter": 7,
      "venus": 5,
      "saturn": 5,
      "ascendant": 0,
      "total": 37
    },
    "aquarius": {
      "sun": 3,
      "moon": 1,
      "mars": 2,
      "mercury": 2,
      "jupiter": 4,
      "venus": 4,
      "saturn": 3,
      "ascendant": 0,
      "total": 19
    },
    "pisces": {
      "sun": 4,
      "moon": 3,
      "mars": 2,
      "mercury": 4,
      "jupiter": 3,
      "venus": 6,
      "saturn": 2,
      "ascendant": 0,
      "total": 24
    }
  }
}
```


