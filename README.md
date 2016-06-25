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

### advanced_panchang

Provides panchang in details

#### API Endpoint

advanced_panchang

#### Method & URL

| Method | Full URL |
| --- | --- |
| POST | https://api.vedicrishiastro.com/v1/advanced_panchang |

#### We have two types of Panchang APIs

**1\. Panchang at specified date and time**
Here, following APIs are used and date and time along with latitude, longitude and timezone are expected -

*   [1\. basic_panchang](https://www.vedicrishiastro.com/docs/api-ref/15/basic_panchang)
*   [2\. planet_panchang](https://www.vedicrishiastro.com/docs/api-ref/16/planet_panchang)
*   [3\. advanced_panchang](https://www.vedicrishiastro.com/docs/api-ref/19/advanced_panchang)

**2\. Panchang at Sunsrise for given day**
Following APIs should be used for getting the panchang data points at the time of sunrise which are used by traditional calendars-

*   [1\. basic_panchang/sunrise](https://www.vedicrishiastro.com/docs/api-ref/17/basic_panchang/sunrise)
*   [2\. planet_panchang/sunrise](https://www.vedicrishiastro.com/docs/api-ref/18/planet_panchang/sunrise)
*   [2\. advanced_panchang/sunrise](https://www.vedicrishiastro.com/docs/api-ref/20/advanced_panchang/sunrise)
*   [4\. chaughadiya_muhurta](https://www.vedicrishiastro.com/docs/api-ref/21/chaughadiya_muhurta)
*   [5\. hora_muhurta](https://www.vedicrishiastro.com/docs/api-ref/22/hora_muhurta)

**" Here only date along with latitude, longitude and timezone are expected to be passed. No time is required. "**

