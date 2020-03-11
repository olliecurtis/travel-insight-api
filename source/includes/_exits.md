## Aggregated Exits

**POST** `/exits`

> Request samples

```json
{
  "startDate": "string",
  "endDate": "string",
  "filter": "string",
  "groupBy": ["string"]
}
```

> Response samples

```json
{
  "results": [
    {
      "dimensions": [
        {
          "name": "market",
          "value": "SG"
        }
      ],
      "aggregations": "count"
    }
  ]
}
```

**/exits** endpoint supports 2 types of queries

- group by **date**
  
  -	For this type of query users don’t have to provide any dimension in groupBy query parameter.
  
  - Returned response will have results grouped by date
  
  - Example: 

    <pre class="center-column-bullet"><strong>Request:</strong><br />curl -X POST https://www.skyscanner.net/g/travel-insight-api/api/aggregation/exits<br />with JSON body:<br />{<br /> "startDate": "2019-12-25",<br /> "endDate": "2019-12-26",<br /> "filter": "{market=SG}"<br />}<br />and your API-Key set in <strong>request headers</strong>.<br /><br />===========================================<br /><br /><strong>Response:<br /></strong>HTTP/1.1 200 OK<strong><br /></strong>Content-Type: application/json; charset=UTF-8<br /><br />{<br />  "results": [<br />    {<br />      "dimensions": [<br />        {<br />          "name": "date",<br />          "value": "2019-12-25",<br />        }<br />      ],<br />      "aggregations": [<br />        {<br />          "name": "count",<br />          "value": 1500<br />        }<br />      ]<br />    },<br />    {<br />      "dimensions": [<br />        {<br />          "name": "date",<br />          "value": "2019-12-26",<br />        }<br />      ],<br />      "aggregations": [<br />        {<br />          "name": "count",<br />          "value": 2000<br />        }<br />      ]<br />    }<br />  ]<br />}</pre>
  
- group by multiple dimension (supported: 3 max)
  
  -	For this type of query users can specify up to 3 dimensions in groupBy query
  
  - Returned response will have results grouped by provided dimensions
  
  - Example: 

    <pre class="center-column-bullet"><strong>Request:</strong><br />curl -X POST https://www.skyscanner.net/g/travel-insight-api/api/aggregation/exits<br />with JSON body:<br />{<br /> "startDate": "2019-12-25",<br /> "endDate": "2019-12-26",<br /> "filter": "{market=SG}",<br /> "groupBy": ["<span>originIATA</span>", "<span>destinationIATA</span>"]<br />}<br />and your API-Key set in <strong>request headers</strong>.<br /><br />===========================================<br /><br /><strong>Response:<br /></strong>HTTP/1.1 200 OK<strong><br /></strong>Content-Type: application/json; charset=UTF-8<br /><br />{<br />  "results": [<br />    {<br />      "dimensions": [<br />        {<br />          "name": "<span>originIATA</span>",<br />          "value": "LHR",<br />        },<br />        {<br />          "name": "<span>destinationIATA</span>",<br />          "value": "CDG",<br />        }<br />      ],<br />      "aggregations": [<br />        {<br />          "name": "count",<br />          "value": 2134<br />        }<br />      ]<br />    },<br />    {<br />      "dimensions": [<br />        {<br />          "name": "originIATA",<br />          "value": "SIN",<br />        },<br />        {<br />          "name": "destinationIATA",<br />          "value": "LHR",<br />        }<br />      ],<br />      "aggregations": [<br />        {<br />          "name": "count",<br />          "value": 2000<br />        }<br />      ]<br />    },<br />    {<br />      "dimensions": [<br />        {<br />          "name": "&ldquo;originIATA&rdquo;",<br />          "value": "CDG",<br />        },<br />        {<br />          "name": "&ldquo;destinationIATA&rdquo;",<br />          "value": "LHR",<br />        }<br />      ],<br />      "aggregations": [<br />        {<br />          "name": "count",<br />          "value": 1200<br />        }<br />      ]<br />    }<br />  ]<br />}</pre>

In both type of queries only `startDate` and `endDate` are mandatory query parameters.

`filter` and `groupBy` query parameters, on the other hand, are optional.

Supported filter format can be expressed with the following grammar:

<pre class="center-column"><strong>EBNF grammar for filter structure:</strong><br /><br />&lt;filter&gt; ::= "{" &lt;fieldTokens&gt; ("," &lt;fieldTokens&gt;)* "}";<br /><br />&lt;fieldTokens&gt; ::= &lt;fieldName&gt; "=" &lt;fieldValue&gt; | &lt;fieldRangeToken&gt;;<br /><br />&lt;fieldRangeToken&gt; ::= &lt;fieldName&gt; ("<" | "<=" | ">" | ">=") &lt;value&gt;;<br /><br />&lt;fieldValue&gt; ::= valueToken;<br /><br />&lt;valueToken&gt; ::= &lt;value&gt; | "(" &lt;value&gt; (&lt;operator&gt; valueToken)* ")"<br /><br />&lt;operator&gt; ::= "|";<br /><br />&lt;fieldName&gt; ::= "originCountry" | "<span>destinationCountry</span>" | "<span>originIATA</span>" | "<span>destinationIATA</span>" | "<span>market</span>" <br /> | "<span>cabinClass</span>" | "<span>departureDate</span>" | "<span>returnDate</span>" | "<span>pax</span>" | "<span>route</span>" | "<span>kind</span>" |  "<span>departureTimeOfDay"<br /></span> | "<span>returnTimeOfDay" | "marketingCarriers" | "stops" </span>;<br /><br />&lt;value&gt; ::= string | integer | date | datetime;<br /><br /><br /><strong>Semantics:<br /></strong>&lt;operator&gt; "|" represents logical OR (||)<strong><br />EBNF syntax:</strong> * for "zero or more" occurrences<br /><br />Range operators allowed only for pax, stops, departureDate, returnDate<br /><br /><strong>Example:</strong> filter={market=(UK|FR),<span>originIATA</span>=LHR,<span>destinationIATA</span>=(CDG|ORY),<span>pax</span>>1,<span>pax</span><=5}</pre>

<font color="red">*Please note that there should not be any spaces between filter tokens*</font>

### Responses

| Code | Description |
| ---- | ----------- |
| 200 | Aggregated results returned |
| 400 | Request validation failure -  Invalid input syntax |
| 401 | Unsuccessful authentication |
| 422 | Request validation failure - Malformed semantics in input |
| 429 | Too many requests |
| 500 | Failure to process the request |
