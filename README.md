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
| day      | int | Chaughadiya day, eg: 10 |
| month     | int      |   Chaughadiya month, eg:5 |
| year | int      |    Chaughadiya year, eg:2015 |
| lat | float | Chaughadiya place latitude, eg: 19.234|
| lon | float | Chaughadiya place longitude, eg: 72.843|
| tzone | float | Chaughadiya place timezone, eg: 5.5|

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
| day      | int | Hora day, eg: 10 |
| month     | int      |   Hora month, eg:5 |
| year | int      |    Hora year, eg:2015 |
| lat | float | Hora place latitude, eg: 19.234|
| lon | float | Hora place longitude, eg: 72.843|
| tzone | float | Hora place timezone, eg: 5.5|

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
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|

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
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|

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

## Basic Astro
This package contains basic astrological details. Planetary configurations such as full degrees, normalised degrees, house position , nakshatra name, house lord and other details.

### birth_details
Along with birth details it provides sunrise, sunset, ayanamsha.

#### API Endpoint
birth_details

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/birth_details |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "year": 1992,
  "month": 7,
  "day": 22,
  "hour": 9,
  "minute": 21,
  "latitude": 25.31668,
  "longitude": 83.01042,
  "timezone": 5.5,
  "sunrise": "5:21:28",
  "sunset": "18:49:35",
  "ayanamsha": 23.753052294684778
}
```

### astro_details
Provides the complete avakahada details e.g. nakshtatra, charan, tithe, karan, yog ,varna, vashaya

#### API Endpoint
astro_details

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/astro_details |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "Varna": "Kshatriya",
  "Vashya": "Chatuspad",
  "Yoni": "Gaj",
  "Gan": "Manushya",
  "Nadi": "Madhya",
  "SignLord": "Mars",
  "sign": "Aries",
  "Naksahtra": "Bharni",
  "NaksahtraLord": "Venus",
  "Charan": 3,
  "Yog": "Dhriti",
  "Karan": "Baalav",
  "Tithi": "Krishna Ekadashi",
  "yunja": "Poorva",
  "tatva": "Fire",
  "name_alphabet": "Le",
  "paya": "Gold"
}
```

### planets
Full planetary positions including ascendant along with retrograde status and nakshatra, house, sign

#### API Endpoint
planets

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/planets |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
[
  {
    "id": 0,
    "name": "Sun",
    "fullDegree": 75.01867995815415,
    "normDegree": 15.018679958154152,
    "speed": 0.9536705592639696,
    "isRetro": "false",
    "sign": "Gemini",
    "signLord": "Mercury",
    "nakshatra": "Ardra",
    "nakshatraLord": "Rahu",
    "house": 8
  },
  {
    "id": 1,
    "name": "Moon",
    "fullDegree": 21.349425872500603,
    "normDegree": 21.349425872500603,
    "speed": 14.508795375227711,
    "isRetro": "false",
    "sign": "Aries",
    "signLord": "Mars",
    "nakshatra": "Bharni",
    "nakshatraLord": "Venus",
    "house": 6
  },
  {
    "id": 2,
    "name": "Mars",
    "fullDegree": 208.9733013285976,
    "normDegree": 28.973301328597614,
    "speed": 0.006922409248668087,
    "isRetro": "false",
    "sign": "Libra",
    "signLord": "Venus",
    "nakshatra": "Vishakha",
    "nakshatraLord": "Jupiter",
    "house": 12
  },
  {
    "id": 3,
    "name": "Mercury",
    "fullDegree": 66.99705831618833,
    "normDegree": 6.99705831618833,
    "speed": 2.1177691946516783,
    "isRetro": "false",
    "sign": "Gemini",
    "signLord": "Mercury",
    "nakshatra": "Ardra",
    "nakshatraLord": "Rahu",
    "house": 8
  },
  {
    "id": 4,
    "name": "Jupiter",
    "fullDegree": 142.918341542849,
    "normDegree": 22.918341542848992,
    "speed": 0.1342132692506382,
    "isRetro": "false",
    "sign": "Leo",
    "signLord": "Sun",
    "nakshatra": "Purva Phalguni",
    "nakshatraLord": "Venus",
    "house": 10
  },
  {
    "id": 5,
    "name": "Venus",
    "fullDegree": 81.47939061863748,
    "normDegree": 21.47939061863748,
    "speed": 1.2289210832023776,
    "isRetro": "false",
    "sign": "Gemini",
    "signLord": "Mercury",
    "nakshatra": "Punarvasu",
    "nakshatraLord": "Jupiter",
    "house": 8
  },
  {
    "id": 6,
    "name": "Saturn",
    "fullDegree": 227.1367070622203,
    "normDegree": 17.136707062220296,
    "speed": -0.06081092063358652,
    "isRetro": "true",
    "sign": "Scorpio",
    "signLord": "Mars",
    "nakshatra": "Jyeshtha",
    "nakshatraLord": "Mercury",
    "house": 1
  },
  {
    "id": 7,
    "name": "Rahu",
    "fullDegree": 141.91126603349858,
    "normDegree": 21.911266033498578,
    "speed": -0.05295380733459039,
    "isRetro": "true",
    "sign": "Leo",
    "signLord": "Sun",
    "nakshatra": "Purva Phalguni",
    "nakshatraLord": "Venus",
    "house": 10
  },
  {
    "id": 8,
    "name": "Ketu",
    "fullDegree": 321.9112660334986,
    "normDegree": 21.911266033498578,
    "speed": -0.05295380733459039,
    "isRetro": "true",
    "sign": "Aquarius",
    "signLord": "Saturn",
    "nakshatra": "Purva Bhadrapad",
    "nakshatraLord": "Jupiter",
    "house": 4
  },
  {
    "id": 9,
    "name": "Ascendant",
    "fullDegree": 226.9999482337994,
    "normDegree": 16.999948233799387,
    "speed": 0,
    "isRetro": false,
    "sign": "Scorpio",
    "signLord": "Mars",
    "nakshatra": "Jyeshtha",
    "nakshatraLord": "Mercury",
    "house": 1
  }
]
```

### planets/extended
Full planetary positions including ascendant along with,neptune,pluto,uranus, retrograde status and nakshatra, house, sign

#### API Endpoint
planets/extended

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/planets/extended |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
[
  {
    "id": 0,
    "name": "Sun",
    "fullDegree": 75.01867995815415,
    "normDegree": 15.018679958154152,
    "speed": 0.9536705592639696,
    "isRetro": "false",
    "sign": "Gemini",
    "signLord": "Mercury",
    "nakshatra": "Ardra",
    "nakshatraLord": "Rahu",
    "house": 8
  },
  {
    "id": 1,
    "name": "Moon",
    "fullDegree": 21.349425872500603,
    "normDegree": 21.349425872500603,
    "speed": 14.508795375227711,
    "isRetro": "false",
    "sign": "Aries",
    "signLord": "Mars",
    "nakshatra": "Bharni",
    "nakshatraLord": "Venus",
    "house": 6
  },
  {
    "id": 2,
    "name": "Mars",
    "fullDegree": 208.9733013285976,
    "normDegree": 28.973301328597614,
    "speed": 0.006922409248668087,
    "isRetro": "false",
    "sign": "Libra",
    "signLord": "Venus",
    "nakshatra": "Vishakha",
    "nakshatraLord": "Jupiter",
    "house": 12
  },
  {
    "id": 3,
    "name": "Mercury",
    "fullDegree": 66.99705831618833,
    "normDegree": 6.99705831618833,
    "speed": 2.1177691946516783,
    "isRetro": "false",
    "sign": "Gemini",
    "signLord": "Mercury",
    "nakshatra": "Ardra",
    "nakshatraLord": "Rahu",
    "house": 8
  },
  {
    "id": 4,
    "name": "Jupiter",
    "fullDegree": 142.918341542849,
    "normDegree": 22.918341542848992,
    "speed": 0.1342132692506382,
    "isRetro": "false",
    "sign": "Leo",
    "signLord": "Sun",
    "nakshatra": "Purva Phalguni",
    "nakshatraLord": "Venus",
    "house": 10
  },
  {
    "id": 5,
    "name": "Venus",
    "fullDegree": 81.47939061863748,
    "normDegree": 21.47939061863748,
    "speed": 1.2289210832023776,
    "isRetro": "false",
    "sign": "Gemini",
    "signLord": "Mercury",
    "nakshatra": "Punarvasu",
    "nakshatraLord": "Jupiter",
    "house": 8
  },
  {
    "id": 6,
    "name": "Saturn",
    "fullDegree": 227.1367070622203,
    "normDegree": 17.136707062220296,
    "speed": -0.06081092063358652,
    "isRetro": "true",
    "sign": "Scorpio",
    "signLord": "Mars",
    "nakshatra": "Jyeshtha",
    "nakshatraLord": "Mercury",
    "house": 1
  },
  {
    "id": 7,
    "name": "Rahu",
    "fullDegree": 141.91126603349858,
    "normDegree": 21.911266033498578,
    "speed": -0.05295380733459039,
    "isRetro": "true",
    "sign": "Leo",
    "signLord": "Sun",
    "nakshatra": "Purva Phalguni",
    "nakshatraLord": "Venus",
    "house": 10
  },
  {
    "id": 8,
    "name": "Ketu",
    "fullDegree": 321.9112660334986,
    "normDegree": 21.911266033498578,
    "speed": -0.05295380733459039,
    "isRetro": "true",
    "sign": "Aquarius",
    "signLord": "Saturn",
    "nakshatra": "Purva Bhadrapad",
    "nakshatraLord": "Jupiter",
    "house": 4
  },
  {
    "id": 9,
    "name": "Uranus",
    "fullDegree": 0.07398734010829626,
    "normDegree": 0.07398734010829626,
    "speed": 0.023347690928066378,
    "isRetro": "false",
    "sign": "Aries",
    "signLord": "Mars",
    "nakshatra": "Ashwini",
    "nakshatraLord": "Ketu",
    "house": 6
  },
  {
    "id": 10,
    "name": "Neptune",
    "fullDegree": 317.8804645006421,
    "normDegree": 17.88046450064212,
    "speed": -0.008730756309788675,
    "isRetro": "true",
    "sign": "Aquarius",
    "signLord": "Saturn",
    "nakshatra": "Shatbhisha",
    "nakshatraLord": "Rahu",
    "house": 4
  },
  {
    "id": 11,
    "name": "Pluto",
    "fullDegree": 262.3049584494822,
    "normDegree": 22.30495844948223,
    "speed": -0.024507476510135368,
    "isRetro": "true",
    "sign": "Sagittarius",
    "signLord": "Jupiter",
    "nakshatra": "Purva Shadha",
    "nakshatraLord": "Venus",
    "house": 2
  },
  {
    "id": 12,
    "name": "Ascendant",
    "fullDegree": 226.9999482337994,
    "normDegree": 16.999948233799387,
    "speed": 0,
    "isRetro": false,
    "sign": "Scorpio",
    "signLord": "Mars",
    "nakshatra": "Jyeshtha",
    "nakshatraLord": "Mercury",
    "house": 1
  }
]
```


### planets/tropical
Full planetary positions including ascendant along with,neptune,pluto,uranus, retrograde status and nakshatra, house, sign

#### API Endpoint
planets/tropical

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/planets/tropical |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
[
  {
    "name": "Sun",
    "fullDegree": 99.1050399130805,
    "normDegree": 9.105039913080503,
    "speed": 0.9536792374523747,
    "isRetro": "false",
    "sign": "Cancer",
    "house": 8
  },
  {
    "name": "Moon",
    "fullDegree": 45.43578582742696,
    "normDegree": 15.435785827426962,
    "speed": 14.508803543221283,
    "isRetro": "false",
    "sign": "Taurus",
    "house": 6
  },
  {
    "name": "Mars",
    "fullDegree": 233.05966128352392,
    "normDegree": 23.059661283523923,
    "speed": 0.006931346565207917,
    "isRetro": "false",
    "sign": "Scorpio",
    "house": 12
  },
  {
    "name": "Mercury",
    "fullDegree": 91.08341827111468,
    "normDegree": 1.083418271114681,
    "speed": 2.1177778714756146,
    "isRetro": "false",
    "sign": "Cancer",
    "house": 8
  },
  {
    "name": "Jupiter",
    "fullDegree": 167.00470149777536,
    "normDegree": 17.004701497775358,
    "speed": 0.13422175459680458,
    "isRetro": "false",
    "sign": "Virgo",
    "house": 10
  },
  {
    "name": "Venus",
    "fullDegree": 105.56575057356383,
    "normDegree": 15.565750573563832,
    "speed": 1.228929722803493,
    "isRetro": "false",
    "sign": "Cancer",
    "house": 8
  },
  {
    "name": "Saturn",
    "fullDegree": 251.22306701714663,
    "normDegree": 11.223067017146633,
    "speed": -0.06080233543846638,
    "isRetro": "true",
    "sign": "Sagittarius",
    "house": 1
  },
  {
    "name": "Rahu",
    "fullDegree": 24.16034729503465,
    "normDegree": 24.16034729503465,
    "speed": 0.023356277817296992,
    "isRetro": "false",
    "sign": "Aries",
    "house": 5
  },
  {
    "name": "Ketu",
    "fullDegree": 341.9668244555685,
    "normDegree": 11.966824455568485,
    "speed": -0.008722211638006301,
    "isRetro": "true",
    "sign": "Pisces",
    "house": 4
  },
  {
    "name": "Uranus",
    "fullDegree": 286.3913184044086,
    "normDegree": 16.391318404408594,
    "speed": -0.02449873391267724,
    "isRetro": "true",
    "sign": "Capricorn",
    "house": 2
  },
  {
    "name": "Ascendant",
    "fullDegree": 251.08743445798456,
    "normDegree": 11.087434457984557,
    "speed": "-",
    "isRetro": false,
    "sign": "Sagittarius",
    "house": 1
  }
]
```

## Basic Char Dasha
Get the sequence of all Char Dasha

### major_chardasha
Get the complete Major Char Dasha periods along with start and end dates for the given birth detail.

#### API Endpoint
major_chardasha

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/major_chardasha |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
[
  {
    "sign_id": 7,
    "sign_name": "Scorpio",
    "duration": "11 Years",
    "start_date": "30-6-2016",
    "end_date": "30-6-2027"
  },
  {
    "sign_id": 6,
    "sign_name": "Libra",
    "duration": "8 Years",
    "start_date": "30-6-2027",
    "end_date": "30-6-2035"
  },
  {
    "sign_id": 5,
    "sign_name": "Virgo",
    "duration": "3 Years",
    "start_date": "30-6-2035",
    "end_date": "30-6-2038"
  },
  {
    "sign_id": 4,
    "sign_name": "Leo",
    "duration": "2 Years",
    "start_date": "30-6-2038",
    "end_date": "30-6-2040"
  },
  {
    "sign_id": 3,
    "sign_name": "Cancer",
    "duration": "3 Years",
    "start_date": "30-6-2040",
    "end_date": "30-6-2043"
  },
  {
    "sign_id": 2,
    "sign_name": "Gemini",
    "duration": "12 Years",
    "start_date": "30-6-2043",
    "end_date": "30-6-2055"
  },
  {
    "sign_id": 1,
    "sign_name": "Taurus",
    "duration": "1 Years",
    "start_date": "30-6-2055",
    "end_date": "30-6-2056"
  },
  {
    "sign_id": 0,
    "sign_name": "Aries",
    "duration": "6 Years",
    "start_date": "30-6-2056",
    "end_date": "30-6-2062"
  },
  {
    "sign_id": 11,
    "sign_name": "Pisces",
    "duration": "7 Years",
    "start_date": "30-6-2062",
    "end_date": "30-6-2069"
  },
  {
    "sign_id": 10,
    "sign_name": "Aquarius",
    "duration": "6 Years",
    "start_date": "30-6-2069",
    "end_date": "30-6-2075"
  },
  {
    "sign_id": 9,
    "sign_name": "Capricorn",
    "duration": "2 Years",
    "start_date": "30-6-2075",
    "end_date": "30-6-2077"
  },
  {
    "sign_id": 8,
    "sign_name": "Sagittarius",
    "duration": "8 Years",
    "start_date": "30-6-2077",
    "end_date": "30-6-2085"
  }
]
```

### current_chardasha
Returns the currently undergoing Char Dasha. It provides Major Period, Sub Period and Complete sub-sub period for the current date.

#### API Endpoint
current_chardasha

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/current_chardasha |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "dasha_date": "30-6-2016",
  "major_dasha": {
    "sign_id": 7,
    "sign_name": "Scorpio",
    "duration": "11 Years",
    "start_date": "30-6-2016",
    "end_date": "30-6-2027"
  },
  "sub_dasha": {
    "sign_id": 6,
    "sign_name": "Libra",
    "duration": "11 Months",
    "start_date": "30-6-2016",
    "end_date": "30-5-2017"
  },
  "sub_sub_dasha": {
    "sign_id": 7,
    "sign_name": "Scorpio",
    "start_date": "30-6-2016",
    "end_date": "27-7-2016"
  }
}
```

### sub_chardasha/:sign_name
Get all the sub periods of char dasha for the given major period rashi name in the API variable

#### API Endpoint
sub_chardasha/:sign_name

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/sub_chardasha/:sign_name |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json{
  "major_dasha": {
    "sign_id": 0,
    "sign_name": "Aries",
    "duration": "3 Years",
    "start_date": "16-8-2027",
    "end_date": "16-8-2030"
  },
  "sub_dasha": [
    {
      "sign_id": 1,
      "sign_name": "Taurus",
      "start_date": "16-8-2027",
      "end_date": "16-11-2027",
      "start_ms": 1818388800000,
      "end_ms": 1826341200000
    },
    {
      "sign_id": 2,
      "sign_name": "Gemini",
      "start_date": "16-11-2027",
      "end_date": "16-2-2028",
      "start_ms": 1826341200000,
      "end_ms": 1834290000000
    },
    {
      "sign_id": 3,
      "sign_name": "Cancer",
      "start_date": "16-2-2028",
      "end_date": "16-5-2028",
      "start_ms": 1834290000000,
      "end_ms": 1842062400000
    },
    {
      "sign_id": 4,
      "sign_name": "Leo",
      "start_date": "16-5-2028",
      "end_date": "16-8-2028",
      "start_ms": 1842062400000,
      "end_ms": 1850011200000
    },
    {
      "sign_id": 5,
      "sign_name": "Virgo",
      "start_date": "16-8-2028",
      "end_date": "16-11-2028",
      "start_ms": 1850011200000,
      "end_ms": 1857963600000
    },
    {
      "sign_id": 6,
      "sign_name": "Libra",
      "start_date": "16-11-2028",
      "end_date": "16-2-2029",
      "start_ms": 1857963600000,
      "end_ms": 1865912400000
    },
    {
      "sign_id": 7,
      "sign_name": "Scorpio",
      "start_date": "16-2-2029",
      "end_date": "16-5-2029",
      "start_ms": 1865912400000,
      "end_ms": 1873598400000
    },
    {
      "sign_id": 8,
      "sign_name": "Sagittarius",
      "start_date": "16-5-2029",
      "end_date": "16-8-2029",
      "start_ms": 1873598400000,
      "end_ms": 1881547200000
    },
    {
      "sign_id": 9,
      "sign_name": "Capricorn",
      "start_date": "16-8-2029",
      "end_date": "16-11-2029",
      "start_ms": 1881547200000,
      "end_ms": 1889499600000
    },
    {
      "sign_id": 10,
      "sign_name": "Aquarius",
      "start_date": "16-11-2029",
      "end_date": "16-2-2030",
      "start_ms": 1889499600000,
      "end_ms": 1897448400000
    },
    {
      "sign_id": 11,
      "sign_name": "Pisces",
      "start_date": "16-2-2030",
      "end_date": "16-5-2030",
      "start_ms": 1897448400000,
      "end_ms": 1905134400000
    },
    {
      "sign_id": 0,
      "sign_name": "Aries",
      "start_date": "16-5-2030",
      "end_date": "16-8-2030",
      "start_ms": 1905134400000,
      "end_ms": 1913083200000
    }
  ]
}
```

### sub_chardasha/:majorSign/:subSign
Get all the sub periods of char dasha for the given major period rashi name in the API variable

#### API Endpoint
sub_chardasha/:majorSign/:subSign

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/sub_chardasha/:majorSign/:subSign |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "major_dasha": {
    "sign_id": 0,
    "sign_name": "Aries",
    "duration": "6 Years",
    "start_date": "30-6-2056",
    "end_date": "30-6-2062"
  },
  "sub_dasha": {
    "sign_id": 3,
    "sign_name": "Cancer",
    "duration": "6 Months",
    "start_date": "30-6-2057",
    "end_date": "30-12-2057"
  },
  "sub_sub_dasha": [
    {
      "sign_id": 2,
      "sign_name": "Gemini",
      "start_date": "30-6-2057",
      "end_date": "15-7-2057",
      "start_ms": 2761099200000,
      "end_ms": 2762416800000
    },
    {
      "sign_id": 1,
      "sign_name": "Taurus",
      "start_date": "15-7-2057",
      "end_date": "30-7-2057",
      "start_ms": 2762416800000,
      "end_ms": 2763734400000
    },
    {
      "sign_id": 0,
      "sign_name": "Aries",
      "start_date": "30-7-2057",
      "end_date": "14-8-2057",
      "start_ms": 2763734400000,
      "end_ms": 2765052000000
    },
    {
      "sign_id": 11,
      "sign_name": "Pisces",
      "start_date": "14-8-2057",
      "end_date": "30-8-2057",
      "start_ms": 2765052000000,
      "end_ms": 2766369600000
    },
    {
      "sign_id": 10,
      "sign_name": "Aquarius",
      "start_date": "30-8-2057",
      "end_date": "14-9-2057",
      "start_ms": 2766369600000,
      "end_ms": 2767687200000
    },
    {
      "sign_id": 9,
      "sign_name": "Capricorn",
      "start_date": "14-9-2057",
      "end_date": "29-9-2057",
      "start_ms": 2767687200000,
      "end_ms": 2769004800000
    },
    {
      "sign_id": 8,
      "sign_name": "Sagittarius",
      "start_date": "29-9-2057",
      "end_date": "14-10-2057",
      "start_ms": 2769004800000,
      "end_ms": 2770322400000
    },
    {
      "sign_id": 7,
      "sign_name": "Scorpio",
      "start_date": "14-10-2057",
      "end_date": "30-10-2057",
      "start_ms": 2770322400000,
      "end_ms": 2771640000000
    },
    {
      "sign_id": 6,
      "sign_name": "Libra",
      "start_date": "30-10-2057",
      "end_date": "14-11-2057",
      "start_ms": 2771640000000,
      "end_ms": 2772961200000
    },
    {
      "sign_id": 5,
      "sign_name": "Virgo",
      "start_date": "14-11-2057",
      "end_date": "29-11-2057",
      "start_ms": 2772961200000,
      "end_ms": 2774278800000
    },
    {
      "sign_id": 4,
      "sign_name": "Leo",
      "start_date": "29-11-2057",
      "end_date": "14-12-2057",
      "start_ms": 2774278800000,
      "end_ms": 2775596400000
    },
    {
      "sign_id": 3,
      "sign_name": "Cancer",
      "start_date": "14-12-2057",
      "end_date": "30-12-2057",
      "start_ms": 2775596400000,
      "end_ms": 2776914000000
    }
  ]
}

```


## Basic Gemstone Suggestions
Provides report of Gems and Remedies with Life Stone, Lucky Stone, Benefic Stone, Stone details as per Vimsottari Mahadasha period.

### basic_gem_suggestion
This api recommends life stone,lucky stone,benefic stone.


#### API Endpoint
basic_gem_suggestion

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/basic_gem_suggestion|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "LIFE": {
    "name": "Red Coral",
    "semi_gem": "Red Agate",
    "wear_finger": "Index",
    "weight_caret": "6 - 10.25",
    "wear_metal": "Gold",
    "wear_day": "Tuesday",
    "gem_deity": "Mars"
  },
  "BENEFIC": {
    "name": "Opal",
    "semi_gem": "Opal/Zircon",
    "wear_finger": "Little",
    "weight_caret": "1 - 4.25",
    "wear_metal": "Silver",
    "wear_day": "Friday",
    "gem_deity": "Venus"
  },
  "LUCKY": {
    "name": "Emerald",
    "semi_gem": "Onyx",
    "wear_finger": "Little",
    "weight_caret": " 4 - 6.25",
    "wear_metal": "Gold",
    "wear_day": "Wednesday",
    "gem_deity": "Mercury"
  }
}

```

## Basic Numerology
Provides detailed Numerology report.

### numero_table
Provides detailed Numerology report.

#### API Endpoint
numero_table

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/numero_table|

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| name | float | Your full name e, eg: Ajeet Kanojia|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "name": "Ajeet Kanojia",
  "date": "6-121-2014",
  "destiny_number": 8,
  "radical_number": 6,
  "name_number": 1,
  "evil_num": "1,8",
  "fav_color": "White",
  "fav_day": "Thursday, Tuesday, Friday",
  "fav_god": "Devi",
  "fav_mantra": "|| Om Shum Shukray Namah ||",
  "fav_metal": "Sillver",
  "fav_stone": "Diamond, Opal",
  "fav_substone": "Zircon, White Sapphire",
  "friendly_num": "4,3,9",
  "neutral_num": "2,5,7",
  "radical_num": "6",
  "radical_ruler": "Venus"
}

```

## Basic Panchang
The package consists of the five panchang elements which are day, nakshatra, yog, karan and tithi along with sunrise and sunset timings. This also includes chaugadiya and planetary degrees at that point of time.

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

### basic_panchang

Provides data points for panchang elements.

#### API Endpoint

basic_panchang

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/basic_panchang |

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
  "tithi": "Shukla-Ashtami",
  "yog": "Vaidhriti",
  "nakshatra": "Krittika",
  "karan": "Vishti",
  "sunrise": "7:3:17",
  "sunset": "18:43:38"
}

```

### basic_panchang/sunrise

Provides data points for panchang elements.

#### API Endpoint

basic_panchang/sunrise

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/basic_panchang/sunrise |

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
  "tithi": "Shukla-Ashtami",
  "yog": "Vaidhriti",
  "nakshatra": "Krittika",
  "karan": "Vishti",
  "sunrise": "7:3:17",
  "sunset": "18:43:38"
}

```

### planet_panchang

Provides panchang planetary degrees ,retrograde and positions.

#### API Endpoint

planet_panchang

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/planet_panchang |

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
[
  {
    "id": 0,
    "name": "Sun",
    "fullDegree": 312.30400347269256,
    "normDegree": 12.304003472692557,
    "isRetro": "false",
    "sign": "Aquarius",
    "sign_lord": "Saturn",
    "nakshatra": "Shatbhisha",
    "nakshatra_lord": "Rahu"
  },
  {
    "id": 1,
    "name": "Moon",
    "fullDegree": 37.45112477913563,
    "normDegree": 7.4511247791356325,
    "isRetro": "false",
    "sign": "Taurus",
    "sign_lord": "Venus",
    "nakshatra": "Krittika",
    "nakshatra_lord": "Sun"
  },
  {
    "id": 2,
    "name": "Mars",
    "fullDegree": 340.0086052768496,
    "normDegree": 10.008605276849607,
    "isRetro": "false",
    "sign": "Pisces",
    "sign_lord": "Jupiter",
    "nakshatra": "Uttra Bhadrapad",
    "nakshatra_lord": "Saturn"
  },
  {
    "id": 3,
    "name": "Mercury",
    "fullDegree": 285.56691716258143,
    "normDegree": 15.566917162581433,
    "isRetro": "false",
    "sign": "Capricorn",
    "sign_lord": "Saturn",
    "nakshatra": "Shravan",
    "nakshatra_lord": "Moon"
  },
  {
    "id": 4,
    "name": "Jupiter",
    "fullDegree": 111.19916911928078,
    "normDegree": 21.199169119280782,
    "isRetro": "true",
    "sign": "Cancer",
    "sign_lord": "Moon",
    "nakshatra": "Ashlesha",
    "nakshatra_lord": "Mercury"
  },
  {
    "id": 5,
    "name": "Venus",
    "fullDegree": 341.4409638339589,
    "normDegree": 11.440963833958904,
    "isRetro": "false",
    "sign": "Pisces",
    "sign_lord": "Jupiter",
    "nakshatra": "Uttra Bhadrapad",
    "nakshatra_lord": "Saturn"
  },
  {
    "id": 6,
    "name": "Saturn",
    "fullDegree": 220.60759834888617,
    "normDegree": 10.607598348886171,
    "isRetro": "false",
    "sign": "Scorpio",
    "sign_lord": "Mars",
    "nakshatra": "Anuradha",
    "nakshatra_lord": "Saturn"
  },
  {
    "id": 7,
    "name": "Rahu",
    "fullDegree": 167.93931821066,
    "normDegree": 17.93931821065999,
    "isRetro": "true",
    "sign": "Virgo",
    "sign_lord": "Mercury",
    "nakshatra": "Hast",
    "nakshatra_lord": "Moon"
  },
  {
    "id": 8,
    "name": "Ketu",
    "fullDegree": 347.93931821065996,
    "normDegree": 17.939318210659962,
    "isRetro": "true",
    "sign": "Pisces",
    "sign_lord": "Jupiter",
    "nakshatra": "Revati",
    "nakshatra_lord": "Mercury"
  },
  {
    "id": 9,
    "name": "Asc",
    "fullDegree": 57.565378655311946,
    "normDegree": 27.565378655311946,
    "isRetro": false,
    "sign": "Taurus",
    "sign_lord": "Venus",
    "nakshatra": "Mrigshira",
    "nakshatra_lord": "Mars"
  }
]

```

### planet_panchang/sunrise

Provides panchang planetary degrees and positions for sunrise.

#### API Endpoint

planet_panchang/sunrise

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/planet_panchang/sunrise |

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
[
  {
    "id": 0,
    "name": "Sun",
    "fullDegree": 312.30400347269256,
    "normDegree": 12.304003472692557,
    "isRetro": "false",
    "sign": "Aquarius",
    "sign_lord": "Saturn",
    "nakshatra": "Shatbhisha",
    "nakshatra_lord": "Rahu"
  },
  {
    "id": 1,
    "name": "Moon",
    "fullDegree": 37.45112477913563,
    "normDegree": 7.4511247791356325,
    "isRetro": "false",
    "sign": "Taurus",
    "sign_lord": "Venus",
    "nakshatra": "Krittika",
    "nakshatra_lord": "Sun"
  },
  {
    "id": 2,
    "name": "Mars",
    "fullDegree": 340.0086052768496,
    "normDegree": 10.008605276849607,
    "isRetro": "false",
    "sign": "Pisces",
    "sign_lord": "Jupiter",
    "nakshatra": "Uttra Bhadrapad",
    "nakshatra_lord": "Saturn"
  },
  {
    "id": 3,
    "name": "Mercury",
    "fullDegree": 285.56691716258143,
    "normDegree": 15.566917162581433,
    "isRetro": "false",
    "sign": "Capricorn",
    "sign_lord": "Saturn",
    "nakshatra": "Shravan",
    "nakshatra_lord": "Moon"
  },
  {
    "id": 4,
    "name": "Jupiter",
    "fullDegree": 111.19916911928078,
    "normDegree": 21.199169119280782,
    "isRetro": "true",
    "sign": "Cancer",
    "sign_lord": "Moon",
    "nakshatra": "Ashlesha",
    "nakshatra_lord": "Mercury"
  },
  {
    "id": 5,
    "name": "Venus",
    "fullDegree": 341.4409638339589,
    "normDegree": 11.440963833958904,
    "isRetro": "false",
    "sign": "Pisces",
    "sign_lord": "Jupiter",
    "nakshatra": "Uttra Bhadrapad",
    "nakshatra_lord": "Saturn"
  },
  {
    "id": 6,
    "name": "Saturn",
    "fullDegree": 220.60759834888617,
    "normDegree": 10.607598348886171,
    "isRetro": "false",
    "sign": "Scorpio",
    "sign_lord": "Mars",
    "nakshatra": "Anuradha",
    "nakshatra_lord": "Saturn"
  },
  {
    "id": 7,
    "name": "Rahu",
    "fullDegree": 167.93931821066,
    "normDegree": 17.93931821065999,
    "isRetro": "true",
    "sign": "Virgo",
    "sign_lord": "Mercury",
    "nakshatra": "Hast",
    "nakshatra_lord": "Moon"
  },
  {
    "id": 8,
    "name": "Ketu",
    "fullDegree": 347.93931821065996,
    "normDegree": 17.939318210659962,
    "isRetro": "true",
    "sign": "Pisces",
    "sign_lord": "Jupiter",
    "nakshatra": "Revati",
    "nakshatra_lord": "Mercury"
  },
  {
    "id": 9,
    "name": "Asc",
    "fullDegree": 57.565378655311946,
    "normDegree": 27.565378655311946,
    "isRetro": false,
    "sign": "Taurus",
    "sign_lord": "Venus",
    "nakshatra": "Mrigshira",
    "nakshatra_lord": "Mars"
  }
]

```

## Basic Vimshottari Dasha
Get analysis of precise period of events to come.

### current_vdasha
Provides details of current vimshottari dasha

#### API Endpoint
current_vdasha

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/current_vdasha |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "major": {
    "end": "17-9-2028 14:32",
    "planet": "MERCURY",
    "start": "18-9-2011 11:43"
  },
  "minor": {
    "end": "11-2-2015 7:29",
    "planet": "KETU",
    "start": "14-2-2014 2:43"
  },
  "sub_minor": {
    "end": "22-12-2014 0:0",
    "planet": "SATURN",
    "start": "25-10-2014 15:39"
  },
  "sub_sub_minor": {
    "end": "14-12-2014 8:30",
    "planet": "RAHU",
    "start": "5-12-2014 18:2"
  },
  "sub_sub_sub_minor": {
    "end": "10-12-2014 18:28",
    "planet": "MERCURY",
    "start": "9-12-2014 13:13"
  }
}
```

### current_vdasha_all
Provides details of All Level of current vimshottari dasha

#### API Endpoint
current_vdasha_all

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/current_vdasha_all |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
{
  "major": {
    "dasha_period": [
      {
        "planet": "Rahu",
        "start": "14-1-2013 23:56",
        "end": "15-1-2031 8:34"
      },
      {
        "planet": "Jupiter",
        "start": "15-1-2031 8:34",
        "end": "15-1-2047 5:34"
      },
      {
        "planet": "Saturn",
        "start": "15-1-2047 5:34",
        "end": "14-1-2066 20:1"
      },
      {
        "planet": "Mercury",
        "start": "14-1-2066 20:1",
        "end": "14-1-2083 22:50"
      },
      {
        "planet": "Ketu",
        "start": "14-1-2083 22:50",
        "end": "14-1-2090 15:31"
      },
      {
        "planet": "Venus",
        "start": "14-1-2090 15:31",
        "end": "15-1-2110 11:46"
      },
      {
        "planet": "Sun",
        "start": "15-1-2110 11:46",
        "end": "15-1-2116 22:39"
      },
      {
        "planet": "Moon",
        "start": "15-1-2116 22:39",
        "end": "15-1-2126 8:47"
      },
      {
        "planet": "Mars",
        "start": "15-1-2126 8:47",
        "end": "15-1-2133 1:28"
      }
    ]
  },
  "minor": {
    "planet": {
      "major": "Rahu"
    },
    "dasha_period": [
      {
        "planet": "Rahu",
        "start": "14-1-2013 23:56",
        "end": "28-9-2015 3:38"
      },
      {
        "planet": "Jupiter",
        "start": "28-9-2015 3:38",
        "end": "20-2-2018 17:35"
      },
      {
        "planet": "Saturn",
        "start": "20-2-2018 17:35",
        "end": "27-12-2020 16:9"
      },
      {
        "planet": "Mercury",
        "start": "27-12-2020 16:9",
        "end": "17-7-2023 0:58"
      },
      {
        "planet": "Ketu",
        "start": "17-7-2023 0:58",
        "end": "3-8-2024 13:4"
      },
      {
        "planet": "Venus",
        "start": "3-8-2024 13:4",
        "end": "4-8-2027 6:31"
      },
      {
        "planet": "Sun",
        "start": "4-8-2027 6:31",
        "end": "27-6-2028 23:44"
      },
      {
        "planet": "Moon",
        "start": "27-6-2028 23:44",
        "end": "27-12-2029 20:28"
      },
      {
        "planet": "Mars",
        "start": "27-12-2029 20:28",
        "end": "15-1-2031 8:34"
      }
    ]
  },
  "sub_minor": {
    "planet": {
      "major": "Rahu",
      "minor": "Rahu"
    },
    "dasha_period": [
      {
        "planet": "Rahu",
        "start": "14-1-2013 23:56",
        "end": "11-6-2013 22:5"
      },
      {
        "planet": "Jupiter",
        "start": "11-6-2013 22:5",
        "end": "21-10-2013 9:47"
      },
      {
        "planet": "Saturn",
        "start": "21-10-2013 9:47",
        "end": "26-3-2014 13:10"
      },
      {
        "planet": "Mercury",
        "start": "26-3-2014 13:10",
        "end": "13-8-2014 6:5"
      },
      {
        "planet": "Ketu",
        "start": "13-8-2014 6:5",
        "end": "9-10-2014 18:42"
      },
      {
        "planet": "Venus",
        "start": "9-10-2014 18:42",
        "end": "23-3-2015 3:19"
      },
      {
        "planet": "Sun",
        "start": "23-3-2015 3:19",
        "end": "11-5-2015 10:42"
      },
      {
        "planet": "Moon",
        "start": "11-5-2015 10:42",
        "end": "1-8-2015 15:1"
      },
      {
        "planet": "Mars",
        "start": "1-8-2015 15:1",
        "end": "28-9-2015 3:38"
      }
    ]
  },
  "sub_sub_minor": {
    "planet": {
      "major": "Rahu",
      "minor": "Rahu",
      "sub_minor": "Venus"
    },
    "dasha_period": [
      {
        "planet": "Venus",
        "start": "9-10-2014 18:42",
        "end": "6-11-2014 4:8"
      },
      {
        "planet": "Sun",
        "start": "6-11-2014 4:8",
        "end": "14-11-2014 9:22"
      },
      {
        "planet": "Moon",
        "start": "14-11-2014 9:22",
        "end": "28-11-2014 2:5"
      },
      {
        "planet": "Mars",
        "start": "28-11-2014 2:5",
        "end": "7-12-2014 16:11"
      },
      {
        "planet": "Rahu",
        "start": "7-12-2014 16:11",
        "end": "1-1-2015 7:53"
      },
      {
        "planet": "Jupiter",
        "start": "1-1-2015 7:53",
        "end": "23-1-2015 5:50"
      },
      {
        "planet": "Saturn",
        "start": "23-1-2015 5:50",
        "end": "18-2-2015 6:24"
      },
      {
        "planet": "Mercury",
        "start": "18-2-2015 6:24",
        "end": "13-3-2015 13:13"
      },
      {
        "planet": "Ketu",
        "start": "13-3-2015 13:13",
        "end": "23-3-2015 3:19"
      }
    ]
  },
  "sub_sub_sub_minor": {
    "planet": {
      "major": "Rahu",
      "minor": "Rahu",
      "sub_minor": "Venus",
      "sub_sub_minor": "Ketu"
    },
    "dasha_period": [
      {
        "planet": "Ketu",
        "start": "13-3-2015 13:13",
        "end": "14-3-2015 2:38"
      },
      {
        "planet": "Venus",
        "start": "14-3-2015 2:38",
        "end": "15-3-2015 16:59"
      },
      {
        "planet": "Sun",
        "start": "15-3-2015 16:59",
        "end": "16-3-2015 4:30"
      },
      {
        "planet": "Moon",
        "start": "16-3-2015 4:30",
        "end": "16-3-2015 23:40"
      },
      {
        "planet": "Mars",
        "start": "16-3-2015 23:40",
        "end": "17-3-2015 13:6"
      },
      {
        "planet": "Rahu",
        "start": "17-3-2015 13:6",
        "end": "18-3-2015 23:37"
      },
      {
        "planet": "Jupiter",
        "start": "18-3-2015 23:37",
        "end": "20-3-2015 6:17"
      },
      {
        "planet": "Saturn",
        "start": "20-3-2015 6:17",
        "end": "21-3-2015 18:43"
      },
      {
        "planet": "Mercury",
        "start": "21-3-2015 18:43",
        "end": "23-3-2015 3:19"
      }
    ]
  }
}
```


### major_vdasha
Provides details of Major vimshottari dasha

#### API Endpoint
major_vdasha

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/major_vdasha |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
[
  {
    "planet": "JUPITER",
    "start": "18-1-2010 8:54",
    "end": "18-1-2026 5:55"
  },
  {
    "planet": "SATURN",
    "start": "18-1-2026 5:55",
    "end": "17-1-2045 20:21"
  },
  {
    "planet": "MERCURY",
    "start": "17-1-2045 20:21",
    "end": "17-1-2062 23:10"
  },
  {
    "planet": "KETU",
    "start": "17-1-2062 23:10",
    "end": "17-1-2069 15:52"
  },
  {
    "planet": "VENUS",
    "start": "17-1-2069 15:52",
    "end": "17-1-2089 12:7"
  },
  {
    "planet": "SUN",
    "start": "17-1-2089 12:7",
    "end": "17-1-2095 22:59"
  },
  {
    "planet": "MOON",
    "start": "17-1-2095 22:59",
    "end": "18-1-2105 9:7"
  },
  {
    "planet": "MARS",
    "start": "18-1-2105 9:7",
    "end": "19-1-2112 1:49"
  },
  {
    "planet": "RAHU",
    "start": "19-1-2112 1:49",
    "end": "18-1-2130 10:26"
  }
]
```

### major_vdasha
Provides details of Major vimshottari dasha

#### API Endpoint
major_vdasha

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/major_vdasha |

#### Request Data

| Params        | Data type     | Descriptions  |
| ------------- |:-------------| :-----|
| day      | int | Birth day, eg: 10 |
| month     | int      |   Birth month, eg:5 |
| year | int      |    Birth year, eg:2015 |
| lat | float | Birth place latitude, eg: 19.234|
| lon | float | Birth place longitude, eg: 72.843|
| tzone | float | Birth place timezone, eg: 5.5|

#### Response Data  ![alt text](http://localhost/astrologyapi/img/right-arrow.png "Logo Title Text 1")
```json
[
  {
    "planet": "JUPITER",
    "start": "18-1-2010 8:54",
    "end": "18-1-2026 5:55"
  },
  {
    "planet": "SATURN",
    "start": "18-1-2026 5:55",
    "end": "17-1-2045 20:21"
  },
  {
    "planet": "MERCURY",
    "start": "17-1-2045 20:21",
    "end": "17-1-2062 23:10"
  },
  {
    "planet": "KETU",
    "start": "17-1-2062 23:10",
    "end": "17-1-2069 15:52"
  },
  {
    "planet": "VENUS",
    "start": "17-1-2069 15:52",
    "end": "17-1-2089 12:7"
  },
  {
    "planet": "SUN",
    "start": "17-1-2089 12:7",
    "end": "17-1-2095 22:59"
  },
  {
    "planet": "MOON",
    "start": "17-1-2095 22:59",
    "end": "18-1-2105 9:7"
  },
  {
    "planet": "MARS",
    "start": "18-1-2105 9:7",
    "end": "19-1-2112 1:49"
  },
  {
    "planet": "RAHU",
    "start": "19-1-2112 1:49",
    "end": "18-1-2130 10:26"
  }
]
```

### sub_vdasha/:mahaDashaLord
Provide antardasha details


