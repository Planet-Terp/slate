---
title: PlanetTerp API v1
language_tabs:
  - shell: Shell
  - http: HTTP
  - javascript: JavaScript
  - ruby: Ruby
  - python: Python
  - php: PHP
  - java: Java
  - go: Go
toc_footers: []
includes: []
search: true
highlight_theme: darkula
headingLevel: 2

---

<!-- Generator: Widdershins v4.0.1 -->

<h1 id="planetterp-api">PlanetTerp API v1</h1>
## Introduction
> Select a language above to show examples of using the API in that language.

Welcome to <a href="https://planetterp.com">PlanetTerp</a>'s API. This API provides access to data relating to courses, professors, and grade data at the <a href="https://umd.edu">University of Maryland &mdash; College Park</a> (UMD).<br /><br /> The primary purpose of this API is to provide access to grade data. There is already a student-run API that provides access to professor and grade data: <a href="https://umd.io">umd.io</a>.<br /><br /> The course and professor data on this website was obtained using a combination of umd.io and <a href="https://app.testudo.umd.edu/soc/">UMD's Schedule of Classes</a>. The grade data is from the <a href="https://www.irpa.umd.edu"">UMD Office of Institutional Research, Planning &amp; Assessment</a> (IRPA) and obtained through <a href="https://www.umd.edu/administration/public-information-request">a request</a> under <a href="http://www.marylandattorneygeneral.gov/OpenGov%20Documents/PIA_manual_printable.pdf">the state of Maryland's Public Information Act</a> (PIA).<br /><br/> The base URL of the API is <a href="https://api.planetterp.com/v1">https://api.planetterp.com/v1</a>.<br /><br /> For support, please email <a href="mailto:admin@planetterp.com">admin@planetterp.com</a>.

## Usage
This API does not require any authentication. There are no hard rate limits, but please take a pause between each request.

<h1 id="planetterp-api-courses">Courses</h1>

## Get courses

```shell
# You can also use wget
curl -X GET https://api.planetterp.com/v1/courses?department=MATH&limit=1

```

```http
GET https://api.planetterp.com/v1/courses?department=MATH&limit=1 HTTP/1.1
Host: api.planetterp.com

```

```javascript

fetch('https://api.planetterp.com/v1/courses?department=MATH&limit=1',
{
  method: 'GET'

})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

result = RestClient.get 'https://api.planetterp.com/v1/courses',
  params: {
  'department' => 'string',
'limit' => 'integer'
}

p JSON.parse(result)

```

```python
import requests

r = requests.get('https://api.planetterp.com/v1/courses', params={
  'department': 'MATH',  'limit': '1'
})

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://api.planetterp.com/v1/courses', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.planetterp.com/v1/courses?department=MATH&limit=1");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.planetterp.com/v1/courses", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

Get all courses, in alphabetical order.

`GET https://api.planetterp.com/v1/courses`

<h3 id="get-courses-parameters">Query Parameters</h3>

|Name|Type|Description|
|---|---|---|---|---|
|department|string|<em>Optional.</em> Only get courses in a department. Must be four characters. Default: all departments|
|reviews|boolean|<em>Optional.</em> Show reviews for the course (reviews for professors that taught the course and listed this course as the one being reviewed). Default: <code>false</code>|
|limit|integer|<em>Optional.</em> Maximum number of records to return. Must be between 1 and 1000. Default: <code>100</code>|
|offset|integer|<em>Optional.</em> Number of records to skip for pagination. Default: <code>0</code>|

<!-- 
 -->

<!-- 

<h3 id="get-courses-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns courses matching query|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|bad input parameter|None|

 -->

<!-- <aside class="success">
This operation does not require authentication
</aside>
 -->

<h1 id="planetterp-api-professors">Professors</h1>

## Get a professor

```shell
# You can also use wget
curl -X GET https://api.planetterp.com/v1/professor?name=Jon%20Snow&reviews=true \
  -H 'Accept: application/json'

```

```http
GET https://api.planetterp.com/v1/professor?name=Jon%20Snow&reviews=true HTTP/1.1
Host: api.planetterp.com
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('https://api.planetterp.com/v1/professor?name=Jon%20Snow&reviews=true',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.planetterp.com/v1/professor',
  params: {
  'name' => 'string',
'reviews' => 'boolean'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.planetterp.com/v1/professor', params={
  'name': 'Jon Snow',  'reviews': 'true'
}, headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://api.planetterp.com/v1/professor', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.planetterp.com/v1/professor?name=Jon%20Snow&reviews=true");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.planetterp.com/v1/professor", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

Get a professor.

`GET https://api.planetterp.com/v1/professor`

<h3 id="get-a-professor-parameters">Query Parameters</h3>

|Name|Type|Description|
|---|---|---|---|---|
|name|string|<strong>Required.</strong> Show the given professor.|
|reviews|boolean|<em>Optional.</em> Show reviews for the professor. Default: <code>false</code>|

<!-- 
 -->

<!-- 

> Example responses

> 200 Response

```json
[
  {
    "name": "Jon Snow",
    "slug": "snow",
    "type": "professor",
    "courses": [
      "MATH140"
    ]
  }
]
```

<h3 id="get-a-professor-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns professors matching query|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|bad input parameter|None|

<h3 id="get-a-professor-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|
|---|---|---|---|---|
|*anonymous*|[[Professor](#schemaprofessor)]|false|none|none|
|» name|string|true|none|none|
|» slug|string|true|none|none|
|» type|string|true|none|none|
|» courses|[string]|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|professor|
|type|ta|

 -->

<!-- <aside class="success">
This operation does not require authentication
</aside>
 -->

## Get all professors

```shell
# You can also use wget
curl -X GET https://api.planetterp.com/v1/professors?reviews=true&limit=1 \
  -H 'Accept: application/json'

```

```http
GET https://api.planetterp.com/v1/professors?reviews=true&limit=1 HTTP/1.1
Host: api.planetterp.com
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('https://api.planetterp.com/v1/professors?reviews=true&limit=1',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.planetterp.com/v1/professors',
  params: {
  'reviews' => 'boolean',
'limit' => 'integer'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.planetterp.com/v1/professors', params={
  'reviews': 'true',  'limit': '1'
}, headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://api.planetterp.com/v1/professors', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.planetterp.com/v1/professors?reviews=true&limit=1");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.planetterp.com/v1/professors", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

Get all professors, in alphabetical order.

`GET https://api.planetterp.com/v1/professors`

<h3 id="get-all-professors-parameters">Query Parameters</h3>

|Name|Type|Description|
|---|---|---|---|---|
|type|string|<em>Optional.</em> Show only reviews for professors or teaching assistants. Default: show both. Options: <code>professor</code>, <code>ta</code>|
|reviews|boolean|<em>Optional.</em> Show reviews for the professors. Default: <code>false</code>|
|limit|integer|<em>Optional.</em> Maximum number of records to return. Must be between 1 and 1000. Default: <code>100</code>|
|offset|integer|<em>Optional.</em> Number of records to skip for pagination. Default: <code>0</code>|

<!-- 
#### Enumerated Values

|Parameter|Value|
|---|---|
|type|professor|
|type|ta|

 -->

<!-- 

> Example responses

> 200 Response

```json
[
  {
    "name": "Jon Snow",
    "slug": "snow",
    "type": "professor",
    "courses": [
      "MATH140"
    ]
  }
]
```

<h3 id="get-all-professors-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns professors matching query|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|bad input parameter|None|

<h3 id="get-all-professors-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|
|---|---|---|---|---|
|*anonymous*|[[Professor](#schemaprofessor)]|false|none|none|
|» name|string|true|none|none|
|» slug|string|true|none|none|
|» type|string|true|none|none|
|» courses|[string]|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|professor|
|type|ta|

 -->

<!-- <aside class="success">
This operation does not require authentication
</aside>
 -->

<h1 id="planetterp-api-grades">Grades</h1>

## Get grades

```shell
# You can also use wget
curl -X GET https://api.planetterp.com/v1/grades?professor=Jon%20Snow&semester=202001 \
  -H 'Accept: application/json'

```

```http
GET https://api.planetterp.com/v1/grades?professor=Jon%20Snow&semester=202001 HTTP/1.1
Host: api.planetterp.com
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('https://api.planetterp.com/v1/grades?professor=Jon%20Snow&semester=202001',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.planetterp.com/v1/grades',
  params: {
  'professor' => 'string',
'semester' => 'string'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.planetterp.com/v1/grades', params={
  'professor': 'Jon Snow',  'semester': '202001'
}, headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://api.planetterp.com/v1/grades', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.planetterp.com/v1/grades?professor=Jon%20Snow&semester=202001");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.planetterp.com/v1/grades", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

Get grades for a course, professor, or both. This endpoint returns all of the grades available by section.

`GET https://api.planetterp.com/v1/grades`

<h3 id="get-grades-parameters">Query Parameters</h3>

|Name|Type|Description|
|---|---|---|---|---|
|course|string|<em>Optional.</em> Show only grades for the given course.|
|professor|string|<em>Optional.</em> Show only grades for the given professor.|
|semester|string|<em>Optional.</em> Show only grades for the given semester. Semester should be provided as the year followed by the semester code. `01` means Spring and `08` means Fall. For example, `202001` means Spring 2020. Default: all semesters|

<!-- 
 -->

<!-- 

> Example responses

> 200 Response

```json
[
  {
    "course": "MATH140",
    "professor": "Jon Snow",
    "semester": "202001",
    "section": "0101",
    "A+": 1,
    "A": 1,
    "A-": 1,
    "B+": 1,
    "B": 1,
    "B-": 1,
    "C+": 1,
    "C": 1,
    "C-": 1,
    "D+": 1,
    "D": 1,
    "D-": 1,
    "F": 1,
    "W": 1,
    "Other": 1
  }
]
```

<h3 id="get-grades-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns grades matching query|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|bad input parameter|None|

<h3 id="get-grades-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|
|---|---|---|---|---|
|*anonymous*|[[Grades](#schemagrades)]|false|none|none|
|» course|string|true|none|none|
|» professor|string|true|none|none|
|» semester|string|true|none|none|
|» section|string|true|none|none|
|» A+|integer|true|none|none|
|» A|integer|true|none|none|
|» A-|integer|true|none|none|
|» B+|integer|true|none|none|
|» B|integer|true|none|none|
|» B-|integer|true|none|none|
|» C+|integer|true|none|none|
|» C|integer|true|none|none|
|» C-|integer|true|none|none|
|» D+|integer|true|none|none|
|» D|integer|true|none|none|
|» D-|integer|true|none|none|
|» F|integer|true|none|none|
|» W|integer|true|none|none|
|» Other|integer|true|none|none|

 -->

<!-- <aside class="success">
This operation does not require authentication
</aside>
 -->

