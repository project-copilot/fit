# Technical Reference: Google FIT Rest API
## Title: Technical Reference: Google FIT Rest API
### Initial content:

#### Overview

Source: 
[REST API  |  Google Fit  |  Google for Developers](https://developers.google.com/fit/rest)

##### REST API

![FIT-1](/step2-project-copilot-project/confluence/google-fit-rest-api.png)

Figure 1: Google Fit REST API.
The Google Fit REST API enables you to store and read health and wellness data in the fitness store from apps on any platform.
The REST API provides resources and methods to:
* Create, obtain, list, and modify **data sources**. A data source represents a unique source of sensor data. All health and wellness data in the fitness store is associated with a particular data source.
* Create, obtain, aggregate, and delete **datasets**. A dataset represents a set of data points from a particular data source.
* List **data points** and add them to a dataset. A data point represents a sample from a particular data source.
* Create, list, and delete **sessions**. A session represents a time interval with associated metadata.

##### Datasets
Source: 
[Working with Datasets  |  Google Fit  |  Google for Developers](https://developers.google.com/fit/rest/v1/datasets) 

##### Working with Datasets
The Fitness REST API lets you create, obtain, and add points to datasets. A dataset represents a set of data points from a particular data source.
Datasets are represented by the Users.dataSources.datasets resource.
**Important**: For best practices when managing user data, see Responsible use of Google Fit.

##### Add points to a dataset
This example demonstrates how to add ten new step count delta points to a previously empty dataset. This example assumes that you created a data source as described in Managing Data Sources.

HTTP method

PATCH

Request URL

https://www.googleapis.com/fitness/v1/users/me/dataSources/
derived:com.google.step_count.delta:1234567890:Example%20Manufacturer:ExampleTablet:1000001
/datasets/1397513334728708316-1397515179728708316

Request body

```json
{
  "dataSourceId":
      "derived:com.google.step_count.delta:1234567890:Example Manufacturer:ExampleTablet:1000001",
  "maxEndTimeNs": 1397515179728708316,
  "minStartTimeNs": 1397513334728708316,
  "point": [
    {
      "dataTypeName": "com.google.step_count.delta",
      "endTimeNanos": 1397513365565713993,
      "originDataSourceId": "",
      "startTimeNanos": 1397513334728708316,
      "value": [
        {
          "intVal": 8
        }
      ]
    },
    {
      "dataTypeName": "com.google.step_count.delta",
      "endTimeNanos": 1397513675197854515,
      "originDataSourceId": "",
      "startTimeNanos": 1397513530098955298,
      "value": [
        {
          "intVal": 3
        }
      ]
    },
    {
      "dataTypeName": "com.google.step_count.delta",
      "endTimeNanos": 1397513764101240710,
      "originDataSourceId": "",
      "startTimeNanos": 1397513817073528237,
      "value": [
        {
          "intVal": 6
        }
      ]
    },
    {
      "dataTypeName": "com.google.step_count.delta",
      "endTimeNanos": 1397513938674093579,
      "originDataSourceId": "",
      "startTimeNanos": 1397514015761859752,
      "value": [
        {
          "intVal": 5
        }
      ]
    },
    {
      "dataTypeName": "com.google.step_count.delta",
      "endTimeNanos": 1397514106400006675,
      "originDataSourceId": "",
      "startTimeNanos": 1397514181893785805,
      "value": [
        {
          "intVal": 4
        }
      ]
    },
    {
      "dataTypeName": "com.google.step_count.delta",
      "endTimeNanos": 1397514304850163634,
      "originDataSourceId": "",
      "startTimeNanos": 1397514356883524220,
      "value": [
        {
          "intVal": 16
        }
      ]
    },
    {
      "dataTypeName": "com.google.step_count.delta",
      "endTimeNanos": 1397514518794639297,
      "originDataSourceId": "",
      "startTimeNanos": 1397514526864527756,
      "value": [
        {
          "intVal": 13
        }
      ]
    },
    {
      "dataTypeName": "com.google.step_count.delta",
      "endTimeNanos": 1397514741275742506,
      "originDataSourceId": "",
      "startTimeNanos": 1397514626480314270,
      "value": [
        {
          "intVal": 18
        }
      ]
    },
    {
      "dataTypeName": "com.google.step_count.delta",
      "endTimeNanos": 1397514813435152213,
      "originDataSourceId": "",
      "startTimeNanos": 1397514839292833196,
      "value": [
        {
          "intVal": 17
        }
      ]
    },
    {
      "dataTypeName": "com.google.step_count.delta",
      "endTimeNanos": 1397515179728708316,
      "originDataSourceId": "",
      "startTimeNanos": 1397515170565969137,
      "value": [
        {
          "intVal": 11
        }
      ]
    }
  ]
}
```

Response

The response is a 200 OK status code. The response body contains an array with JSON representations of all the points that were inserted successfully.

Curl command

$ curl --header "Authorization: Bearer ya29.1.yourtokenvalue" -X PATCH \
--header "Content-Type: application/json;encoding=utf-8" -d @addpoints.json \
"https://www.googleapis.com/fitness/v1/users/me/dataSources/derived:com.google.step_count.delta:1234567890:Example%20Manufacturer:ExampleTablet:1000001/datasets/1397513334728708316-1397515179728708316"
Get a dataset
This example demonstrates how to get the contents of a dataset.

HTTP method

GET

Request URL

https://www.googleapis.com/fitness/v1/users/me/dataSources/
derived:com.google.step_count.delta:1234567890:Example%20Manufacturer:ExampleTablet:1000001
/datasets/1397513334728708316-1397515179728708316

Request body

None.

Response

If the dataset exists, the response is a 200 OK status code. The response body contains a JSON representation of the dataset.

Curl command

$ curl --header "Authorization: Bearer ya29.1.yourtokenvalue" -X GET \
--header "Content-Type: application/json;encoding=utf-8" \
"https://www.googleapis.com/fitness/v1/users/me/dataSources/derived:com.google.step_count.delta:1234567890:Example%20Manufacturer:ExampleTablet:1000001/datasets/1397513334728708316-1397515179728708316"
 
### Actions in Project Copilot:
- Write custom instruction:
```xml
<instruction>...</instruction>
```
### Final content: