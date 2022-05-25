# zerionJS

zerionJS is an easy-to-use API wrapper for Zerion Software's iFormBuilder. The goal of this project--along with its sister Python-based library zerionPy--is to get you working with the iFormBuilder API in minutes instead of hours or days. The library takes care of all access token management; all you need to do is supply valid credentials and the library will request and renew access tokens for the duration of its execution.

# Getting Started

To begin, install the module.

```
npm install zerionJS
```

After the module is installed, import it using the following command in your js file:

```javascript
const IFB = require("zerionJS/ifb");
```

With the module imported, create an API connection with the following two lines:

```javascript
const api = new IFB(SERVER, CLIENT_KEY, CLIENT_SECRET, VERSION, REGION);
await api.init();
```

Note that all methods are asynchronous and require the `await` keyword.

The five parameters listed above are required for every API connection. Below are a list of accepted values for version and region.
| Parameter | Values |
|--------------|-----------|
| VERSION | 6, 8, 8.1 |
| REGION | us, uk, au, hipaa, qa |

In addition to these five required parameters, the following optional attributes may be configured in a params object. Below is a list of possible options.
| Name | Values | Description |
|--------------|-----------|------------|
| simple_response | true/false | when enabled, API calls will return only the response body |
| skip_rate_limit_retry | true/false | when enabled, 429 status codes will be returned instead of automatically retried |

# Making API Calls

This library is designed to make working with Zerion APIs as easy as possible. Each available command/resource combination is available as a distinct method. Methods are named with the following convention: `commandResourceName`. For example, a GET request to the profiles resource is named `getProfiles()`.

Additionally, each method is defined to accept the necessary parameters to properly execute. For example, a GET request to the /records resource will require a profile id as well as page id. A corresponding function call may look like: `api.getRecords(12345, 67890)` where 12345 is the profile id and 67890 is the page id.

Querying a specific resource by ID will generally be done by the singular noun of the resource. For example, a GET request to the /records resource with id `1` would be named `getRecord()` and the function call could look something like: `api.getRecord(12345, 67890, 1)`.

Each 

# How to Contribute

This library is a work in progress. As Zerion APIs are released, this library will be updated. Additionally, functionalities such as additional safeguards for erroneous function calls and improper parameter values may be added in the future. If you have a suggestion or run into any problems, please submit an Issue.

# Change Log

-   May 25, 2022 (v2.0.0)
    -   Initial Release
