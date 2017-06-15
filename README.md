**API Documentation **
**1. Description: List of all dates for which weather information is available as a JSON array.**
**URI:** http://sample-env-1.xfv2hfrwma.us-east-2.elasticbeanstalk.com/historical
**Method:** GET
**Input parameters:** None
**Response Type:** application/json
**Sample Response:**
[{"DATE": "20130101"},
{"DATE": "20130102"}, ......]

**2. Description: Weather information for a particular date. if no information is available - 404 error**
**URI:** http://sample-env-1.xfv2hfrwma.us-east-2.elasticbeanstalk.com/historical/<date>
**Method:** GET
**<date>** String: YYYYMMDD
**Response Type:** application/json
**Sample**
URI: http://sample-env-1.xfv2hfrwma.us-east-2.elasticbeanstalk.com/historical/20151202
Response: {
 "DATE": "20151202", "TMAX": "49", "TMIN": "34"
}
Status code: 200 if data found/ 404 Not Found for an invalid date

**3. Description: Add weather information for a particular day**
**URI:** http://sample-env-1.xfv2hfrwma.us-east-2.elasticbeanstalk.com/historical
**Method:** POST
**Input Type:** (application/json)
**Sample**
Input
 {
  "DATE": "20170227",
  "TMAX": "73.5",
  "TMIN": "57"
}
Status code: 201 if added successfully/ 409 if creating a duplicate/ 406 if invalid date format/ 415 if Unsupprted Input Type

**4. Description: Delete weather info of a particular day**
**URI:** http://sample-env-1.xfv2hfrwma.us-east-2.elasticbeanstalk.com/historical/<date>
**Method:** DELETE
**<date>** String:YYYYMMDD
Status code: 200 Record Delete / 404 Not Found if trying to delete an unexisting record
**Sample**
URI: http://sample-env-1.xfv2hfrwma.us-east-2.elasticbeanstalk.com/historical/20150112
Response: Record Deleted

**5. Description: Weather forecast for next 7 days - the date could be an existing date or future date**
**URI:** http://sample-env-1.xfv2hfrwma.us-east-2.elasticbeanstalk.com/forecast/<date>
**<date>** String: YYYYMMDD
**Response:** Returns the next 7 days Maximum Temperature 
**Response Type:** application/json
**Sample:**
URI: http://sample-env-1.xfv2hfrwma.us-east-2.elasticbeanstalk.com/forecast/20170305
Response:
[
  {
    "DATE": "20170305",
    "TMAX": "49.54",
    "TMIN": "28.87"
  },
  {
    "DATE": "20170306",
    "TMAX": "60.79",
    "TMIN": "30.28"
  },
  {
    "DATE": "20170307",
    "TMAX": "61",
    "TMIN": "46.98"
  },
  {
    "DATE": "20170308",
    "TMAX": "63.7",
    "TMIN": "44.98"
  },
  {
    "DATE": "20170309",
    "TMAX": "50.02",
    "TMIN": "36.2"
  },
  {
    "DATE": "20170310",
    "TMAX": "53.3",
    "TMIN": "29.5"
  },
  {
    "DATE": "20170311",
    "TMAX": "48.62",
    "TMIN": "29.54"
  }
]
