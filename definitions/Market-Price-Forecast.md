# Market Price Forecast
This entity contains a harmonised description of a generic commodity, crop or product price forecast that varies over time (a spot price forecast). This entity is primarily associated with the agricultural vertical and related IoT applications.

| Attribute Name | Attribute Type | Description | Constraint |
|:--- |:--- |:--- |:---:|
| id | @id | Provides a unique identifier for an instance of the entity either in the form of a URI (i.e. either a publicly accessible URL or a URN). | Mandatory |
| type | @type | Defines the type of the entity. | Mandatory |
| createdAt | TemporalProperty | Indicates the date/ time that the instance of the entity was created in ISO 8601 format. The value of this will be set by the server when the entity was created. | Mandatory |
| modifiedAt | TemporalProperty | Indicates the date/ time when the entity was last modified in ISO 8601 format. The value of this will be set by the server when the entity was modified, if the entity has not been modified it may have a null value. | Optional |
| source | Property | Specifies the URL to the source of this data (either organisation or where relevant more specific source) | Recommended |
| dataProvider | Property | Specifies the URL to information about the provider of this information | Recommended |
| entityVersion | Property | The entity specification version as a number. A version number of 2.0 or later denotes the entity is represented using NGSI-LD | Recommended |
| entity | Relationship | Reference to the entity this price forecast relates to e.g. an AgriProduct entity. | Mandatory |
| priceForecast | Property | The market price forecast represented using schema.org PriceSpecification attributes http://schema.org/PriceSpecification | Mandatory |
| address | Property | The market location for this forecast encoded as a Schema.org PostalAddress. https://schema.org/PostalAddress | Mandatory |
| marketScale | Property | Unique code assigned to market scale type. The content includes both a name and a value.

 "Wholesale":Wholesale market price 
"Retail":Retail market price for example
{"name":"Wholesale", 'value':"02"}
or
{"name":"Retail", "value":"01"} | Mandatory |
| weatherForecast | Relationship | A reference to a related weather forecast record | Optional |

## NGSI-LD Context Definition
The following NGSI-LD context definition applies to the **Market Price Forecast** entity

[Download context definition.](../examples/Market-Price-Forecast-context.jsonld)

```JavaScript
{
    "@context": {
        "source": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/source",
        "dataProvider": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/dataprovider",
        "entityVersion": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/entityversion",
        "entity": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/entity",
        "priceForecast": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/priceforecast",
        "address": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/address",
        "marketScale": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/marketscale",
        "weatherForecast": "https://www.gsma.com/iot/iot-big-data/ngsi-ld/weatherforecast"
    }
}
```
## Example of Market Price Forecast Entity
The following is an example instance of the **Market Price Forecast** entity

[Download example entity definition.](../examples/Market-Price-Forecast.jsonld)

```JavaScript
{
    "@context": [
        "https://forge.etsi.org/gitlab/NGSI-LD/NGSI-LD/raw/master/coreContext/ngsi-ld-core-context.json",
        "https://raw.githubusercontent.com/GSMADeveloper/NGSI-LD-Entities/master/examples/Market-Price-Forecast-context.jsonld"
    ],
    "id": "urn:ngsi-ld:MarketPriceForecast:398aa5f4-6a81-4dea-9f85-e9869441a257",
    "type": "MarketPriceForecast",
    "createdAt": "2017-01-01T01:20:00Z",
    "modifiedAt": "2017-05-04T12:30:00Z",
    "source": "https://source.example.com",
    "dataProvider": "https://provider.example.com",
    "entityVersion": 2.0,
    "entity": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:AgriProduct:cdfd9cb8-ae2b-47cb-a43a-b9767ffd5c84"
    },
    "priceForecast": {
        "type": "Property",
        "value": {
            "value": 5,
            "priceCurrency": "USD",
            "validFrom": {
                "value": "2017-08-22T10:18:16Z",
                "@type": "DateTime"
            },
            "validThrough": {
                "value": "2017-08-22T10:18:16Z",
                "@type": "DateTime"
            }
        }
    },
    "address": {
        "type": "Property",
        "value": {
            "@type": "https://schema.org/PostalAddress",
            "addressLocality": "London",
            "addressCountry": "UK"
        }
    },
    "marketScale": {
        "type": "Property",
        "value": {
            "value": "02",
            "marketType": "Wholesale"
        }
    },
    "weatherForecast": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:WeatherForecast:cdfd9cb8-ae2b-47cb-a43a-b9767ffd5c85"
    }
}
```
