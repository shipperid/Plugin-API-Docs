# Shipper Plugin API Documentation

## Contents
 - [Authentication](https://shipperid.github.io/Plugin-API-Docs#Authentication)
 - [Refresh Token](https://shipperid.github.io/Plugin-API-Docs#Refresh-Token)
 - [Create Order](https://shipperid.github.io/Plugin-API-Docs#Create-Order)
 - [Origin Area Dropdown](https://shipperid.github.io/Plugin-API-Docs#Origin-Area-Dropdown)
 - [Destination Area Dropdown](https://shipperid.github.io/Plugin-API-Docs#Destination-Area-Dropdown)
 - [Get Order Detail](https://shipperid.github.io/Plugin-API-Docs#Get-Order-Detail)
 - [Get Order List](https://shipperid.github.io/Plugin-API-Docs#Get-Order-List)
 - Cancel Order
 - Confirm Order
 - Get Provinces Dropdown
 - Get Cities Dropdown
 - Get Suburbs Dropdown
 - Get Areas Dropdown
 
 <br/>
## Authentication

Retrieves Access Token and Expiration information that will be used to request private endpoints.

**Endpont URL**

| Method | URL |
| ------ | ------ |
| POST | plugin-api/v1/auth/tokenize |

**Fields**

| Name | Required | Default | Type | Descroption |
| ------ | ------ | ------ | ------ | ------ |
| grant_type | Y |  | string |  |
| api_key | Y |  | string |  |

**Success Response Example**
 - Code: 200
 - Content: 

 ```javascript
{
    "access_token": "c2f3f69392b088787a667fe261a2da536134393add00bf8889ec9648d6338c23",
    "expires_in": 60,
    "refresh_token": "1be7a903bf04476ba523109e5349ea66"
}
``` 

<br/>
## Refresh Token

Refresh expired access token.

**Endpont URL**

| Method | URL |
| ------ | ------ |
| POST | plugin-api/v1/auth/refreshToken |

**Fields**

| Name | Required | Default | Type | Description |
| ------ | ------ | ------ | ------ | ------ |
| refresh_token | Y |  | string |  |

**Success Response**
 - Code: 200
 - Content: 

 ```javascript
{
    "access_token": "37c00a2318dae8de0a84fcf5df94597b707db0a39974d64d5d0440cfd2971d71",
    "expires_in": 60,
    "refresh_token": "4bc6715af6851b10a74b9478388138be"
}
``` 

<br/>
## Create order

Create Shipper order

**Endpont URL**

| Method | URL | Need Auth |
| ------ | ------ | ------ |
| POST | plugin-api/v1/orders/create | Y |

**Fields**

| Name | Required | Default | Type | Description |
| ------ | ------ | ------ | ------ | ------ |
| csgner_name | Y |  | string |  |
| csgner_phone | Y |  | string |  |
| o_prov_code | Y |  | int |  |
| o_city_code | Y |  | int |  |
| o_sub_code | Y |  | int |  |
| o_area_code | Y |  | int |  |
| o_stop_code | Y |  | int |  |
| o_postal_code | Y |  | int |  |
| o_code | Y |  | int |  |
| o_addr1 | Y |  | string |  |
| o_addr2 | Y |  | string |  |
| o_addr3 | Y |  | string |  |
| csgnee_name | Y |  | string |  |
| csgnee_phone | Y |  | string |  |
| d_ctry_code | Y |  | int |  |
| d_prov_code | Y* |  | int |  |
| d_prov_name | Y* |  | string |  |
| d_city_code | Y* |  | int |  |
| d_city_name | Y* |  | string |  |
| d_sub_code | Y* |  | int |  |
| d_sub_name | Y* |  | string |  |
| d_area_code | Y* |  | int |  |
| d_area_name | Y* |  | string |  |
| d_postal_code | Y |  | int |  |
| d_stop_code | Y |  | string |  |
| d_addr1 | Y |  | string |  |
| d_addr2 | Y |  | string |  |
| d_addr3 | Y |  | string |  |
| pck_type | Y |  | string |  |
| wt | Y |  | int |  |
| w | Y |  | int |  |
| l | Y |  | int |  |
| h | Y |  | int |  |
| content | Y |  | string |  |
| external_code | Y |  | string |  |
| item_price | Y |  | double |  |
| rate_price | Y |  | double |  |
| ins_price | Y |  | double |  |
| payment_type | Y |  | string |  |
| use_ins | Y |  | bool |  |
| is_cod | Y |  | bool |  |
| lgt_code | Y |  | int |  |
| rate_code | Y |  | int |  |
| min_day | Y |  | int |  |
| max_day | Y |  | int |  |
| show_code | Y |  | int |  |

**Request Body Example**

 ```javascript
{
  "csgner_name": "thomson",
  "csgner_phone": "0877123123123",
  "o_prov_code": 34,
  "o_city_code": 475,
  "o_sub_code": 6993,
  "o_area_code": 81215,
  "o_stop_code": 1,
  "o_postal_code": 20118,
  "o_code": 17328,
  "o_addr1": "jalan sudirman",
  "o_addr2": "",
  "o_addr3": "",
  "csgnee_name": "budi",
  "csgnee_phone": "088374837443",
  "d_ctry_code": "",
  "d_prov_code": 11,
  "d_city_code": 113,
  "d_sub_code": 1960,
  "d_area_code": 22153,
  "d_postal_code": 69323,
  "d_stop_code": 5805,
  "d_addr1": "jalan merdeka",
  "d_addr2": "",
  "d_addr3": "",
  "pck_type": "doc",
  "wt": 1,
  "w": 10,
  "l": 10,
  "h": 10,
  "content": "buku",
  "external_code": "buku_budi",
  "item_price": 100000,
  "rate_price": 38000,
  "ins_price": 10000,
  "payment_type": "cash",
  "use_ins": 0,
  "is_cod": "",
  "lgt_code": 1,
  "rate_code": 1,
  "min_day": 3,
  "max_day": 6,
  "show_code": 1
}
``` 

**Success Response**
 - Code: 201
 - Content: 

 ```javascript
{
    "status": "CREATED",
    "message": "Successfully created data.",
    "version": "1.0",
    "items": {
        "created_code": "d5716162044ae9fb29c972baeae681841511868738"
    }
}
``` 

<br/>
## Origin Area Dropdown

Get origin area dropdown.

**Endpont URL**

| Method | URL | Need Auth |
| ------ | ------ | ------ |
| GET | plugin/api/v1/geodata/destDropdown | Y |

**Fields**

| Name | Required | Default | Type | Description |
| ------ | ------ | ------ | ------ | ------ |
| q | Y |  | string | Area keyword |

**Success Response Example**
 - Code: 200
 - Content: 

 ```javascript
{
    "status": "OK",
    "message": "Successfully retreived data.",
    "version": "1.0",
    "items": [
        {
            "label": "Jakarta Barat",
            "value": "42|2"
        },
        {
            "label": "Jakarta Pusat",
            "value": "43|2"
        },
        {
            "label": "Jakarta Selatan",
            "value": "41|2"
        },
        {
            "label": "Jakarta Timur",
            "value": "40|2"
        },
        {
            "label": "Jakarta Utara",
            "value": "39|2"
        },
        {
            "label": "Jakarta Baru, Bula Barat, Seram Bagian Timur, 97554",
            "value": "42253|0"
        },
        {
            "label": "Yogyakarta (Jogjakarta), Gading Rejo, Pringsewu, 35372",
            "value": "38241|0"
        }
    ]
}
``` 

<br/>
## Destination Area Dropdown

Get destination area dropdown.

**Endpont URL**

| Method | URL | Need Auth |
| ------ | ------ | ------ |
| GET | plugin/api/v1/geodata/destDropdown | Y |

**Fields**

| Name | Required | Default | Type | Description |
| ------ | ------ | ------ | ------ | ------ |
| q | Y |  | string | Area keyword |

**Success Response Example**
 - Code: 200
 - Content: 

 ```javascript
{
    "status": "OK",
    "message": "Successfully retreived data.",
    "version": "1.0",
    "items": [
        {
            "label": "Jakarta Barat",
            "value": "42|2"
        },
        {
            "label": "Jakarta Pusat",
            "value": "43|2"
        },
        {
            "label": "Jakarta Selatan",
            "value": "41|2"
        },
        {
            "label": "Jakarta Timur",
            "value": "40|2"
        },
        {
            "label": "Jakarta Utara",
            "value": "39|2"
        },
        {
            "label": "Jakarta Baru, Bula Barat, Seram Bagian Timur, 97554",
            "value": "42253|0"
        },
        {
            "label": "Yogyakarta (Jogjakarta), Gading Rejo, Pringsewu, 35372",
            "value": "38241|0"
        }
    ]
}
``` 

<br/>
## Get Order Detail

Get shipper order detail.

**Endpont URL**

| Method | URL | Need Auth |
| ------ | ------ | ------ |
| GET | plugin/api/v1/orders/detail/{code} | Y |

**Fields**

No query string needed.

**Success Response Example**
 - Code: 200
 - Content: 

 ```javascript
{
    "status": "OK",
    "message": "Successfully retreived data.",
    "version": "1.0",
    "items": [
        {
            "_id": {
                "$id": "5a1d024a3762bdd824000031"
            },
            "id": "1A01159",
            "groupID": null,
            "specialID": "A1159",
            "externalID": "buku_budi",
            "labelChecksum": "3234ad8c0b608b40a7cd21f3bfd4b458",
            "consigner": {
                "id": "5a1cf4473762bdd82400002f",
                "name": "thomson",
                "phoneNumber": "0877123123123"
            },
            "consignee": {
                "id": "5a1cf4473762bdd824000030",
                "name": "budi",
                "phoneNumber": 88374837443
            },
            "batchID": "184b625f96ead90563886cfe431f592a1511850570",
            "awbNumber": "",
            "stickerNumber": "",
            "shipmentStatus": {
                "name": "Order Diterima",
                "description": "Order sudah diterima",
                "statusCode": 1,
                "updatedBy": {
                    "id": "1",
                    "name": "Tetrapack",
                    "plugin_type": "woo",
                    "subscription_level": "1"
                },
                "updateDate": "2017-11-28T07:29:29+00:00"
            },
            "origin": {
                "id": 475,
                "address": "Klinik Dr Indrajana, Jl. Tanah Abang 3 No 23 A, Kel. Pejoto Selatan, Kec.Gambir, 10160",
                "direction": "",
                "postcode": null,
                "stopID": 0,
                "areaID": 0,
                "suburbID": 0,
                "areaName": "",
                "suburbName": "",
                "cityID": 43,
                "cityName": "Jakarta Pusat",
                "provinceID": 6,
                "provinceName": "DKI Jakarta",
                "countryID": 228,
                "countryName": "INDONESIA"
            },
            "destination": {
                "id": 113,
                "address": "Jl. Tipar Gede, Ruko 1 No. 5, Kel. Tipar, Kec. Citamiang, 43141",
                "direction": "",
                "postcode": null,
                "stopID": 0,
                "areaID": 0,
                "suburbID": 0,
                "areaName": "",
                "suburbName": "",
                "cityID": 479,
                "cityName": "Sukabumi, Kota",
                "provinceID": 9,
                "provinceName": "Jawa Barat",
                "countryID": 228,
                "countryName": "INDONESIA"
            },
            "package": {
                "itemType": 178,
                "contents": "buku",
                "price": {
                    "value": 100000,
                    "UoM": "IDR"
                },
                "itemName": "buku",
                "dimension": {
                    "length": {
                        "value": 10,
                        "UoM": "cm"
                    },
                    "height": {
                        "value": 10,
                        "UoM": "cm"
                    },
                    "width": {
                        "value": 10,
                        "UoM": "cm"
                    }
                },
                "weight": {
                    "value": 1,
                    "UoM": "kg"
                },
                "cubicalWeight": {
                    "value": 1,
                    "UoM": "kg"
                },
                "fragile": 1,
                "type": 1,
                "isConfirmed": 0,
                "pictureURL": ""
            },
            "driver": {
                "id": 0,
                "name": "",
                "phoneNumber": "",
                "vehicleType": "",
                "vehicleNumber": "",
                "isPaymentCollected": 0,
                "feedback": {
                    "score": 0,
                    "comment": ""
                },
                "agentID": 0,
                "agentName": ""
            },
            "courier": {
                "id": 1,
                "name": "JNE",
                "rate_id": 1,
                "rate_name": "REG",
                "shipmentType": 1,
                "min_day": 3,
                "max_day": 6,
                "rate": {
                    "value": 38000,
                    "UoM": "IDR"
                },
                "actualRate": {
                    "value": 0,
                    "UoM": "IDR"
                }
            },
            "rates": {
                "shipment": {
                    "value": 38000,
                    "UoM": "IDR"
                },
                "paidShipment": {
                    "value": 0,
                    "UoM": "IDR"
                },
                "actualShipment": {
                    "value": 0,
                    "UoM": "IDR"
                },
                "insurance": {
                    "value": 10000,
                    "UoM": "IDR"
                },
                "paidInsurance": {
                    "value": 0,
                    "UoM": "IDR"
                },
                "actualInsurance": {
                    "value": 0,
                    "UoM": "IDR"
                },
                "escrowCost": {
                    "value": 0,
                    "UoM": "IDR"
                },
                "fulfillmentCost": {
                    "value": 0,
                    "UoM": "IDR"
                },
                "itemPrice": {
                    "value": 100000,
                    "UoM": "IDR"
                }
            },
            "useInsurance": 0,
            "isLabelPrinted": 0,
            "paymentType": "cash",
            "source": "bos",
            "isActive": 1,
            "isAutoTrack": 1,
            "isCustomAWB": 0,
            "readyTime": "2017-11-28T07:29:30+00:00",
            "pickUpTime": "",
            "creationDate": "2017-11-28T07:29:30+00:00",
            "activeDate": "2017-11-28T07:29:30+00:00",
            "lastUpdatedDate": "2017-11-28T06:29:27+00:00",
            "createdBy": 0,
            "shipmentArea": "domestic",
            "cod": {
                "order": 0
            }
        }
    ]
}
``` 

<br/>
## Get Order List

Get its own order list.

**Endpont URL**

| Method | URL | Need Auth |
| ------ | ------ | ------ |
| GET | plugin/api/v1/me/orderList | Y |

**Fields**

No query string needed.

**Success Response Example**
 - Code: 200
 - Content: 

 ```javascript
{
    "status": "OK",
    "message": "Successfully retreived data.",
    "version": "1.0",
    "items": [
        {
            "label": "Jakarta Barat",
            "value": "42|2"
        },
        {
            "label": "Jakarta Pusat",
            "value": "43|2"
        },
        {
            "label": "Jakarta Selatan",
            "value": "41|2"
        },
        {
            "label": "Jakarta Timur",
            "value": "40|2"
        },
        {
            "label": "Jakarta Utara",
            "value": "39|2"
        },
        {
            "label": "Jakarta Baru, Bula Barat, Seram Bagian Timur, 97554",
            "value": "42253|0"
        },
        {
            "label": "Yogyakarta (Jogjakarta), Gading Rejo, Pringsewu, 35372",
            "value": "38241|0"
        }
    ]
}
``` 
