# StichPunks

* Manank Valnad
* Rohit Keshav
* Mehul Mistry
* <insert name>
* <insert name>

## Users

The user collection will store all users and their portfolios. Users will be able to login, and check the state of their investments.

```
{
    "_id":"7b7997a2-c0d2-4f8c-b27a-6a1d4b5b6310",
    "sessionId":"b3988882-627f-4c59-8d5d-54b7a43b030e",
    "hashedPassword":"$2a$08$XdvNkfdNIL8Fq7l8xsuIUeSbNOFgK0M0iV5HOskfVn7.PWncShU.O",
    "profile":{
    	"username": "jdog_43"
        "first_name":"John",
        "last_name":"Doe",
        "_id":"7b7997a2-c0d2-4f8c-b27a-6a1d4b5b6310",
        "amount": 1000
    },
    "verified": True,
    "blocked": False
}
```
<!-- change -->
| Name | Type | Description |
|------|------|-------------|
| _id  | string | A globally unique identifier to represent the user |
| sessionId | string | A globally unique identifier to represent the user's current session |
| hashedPassword | string | A bcrypted string that is a hashed version of the user's password |
| profile | User Profile | The user's profile | 

## User Profile (subdocument; not stored in a separate collection)

This subdocument is used to describe the user's profile.

```
{
    "username": "jdog_43"
    "first_name":"John",
    "last_name":"Doe",
    "_id":"7b7997a2-c0d2-4f8c-b27a-6a1d4b5b6310",
    "amount": 1000
}
```

<!-- change -->
| Name | Type | Description |
|------|------|-------------|
| name | string | The user's name. | 
| hobby | string | A line of text that represents the user's hobby. |
| _id  | string | A globally unique identifier to represent the user |


## Transaction

The transaction collection will store all the transactions that have been initiated.


```
{
    "_id": "5a5c4461-cdc9-4144-84f9-fcb278c5c122",
    "initiator": {
    	"username": "jdog_43",
    	"userID": "7b7997a2-c0d2-4f8c-b27a-6a1d4b5b6310"
    	},
    "title":"usd to btc",
    "transaction": [{
    	"coinName": "btc",
    	"quantity": 2,
    	"buyOrSellAmount": -1000,
    	"valuePerCoin": 500,
    	"stage": "initiated" 	// cancelled, complete
    }]
}
```

<!-- change -->
| Name | Type | Description |
|------|------|-------------|
| _id | string | The task ID. | 
| creator | User Profile | A profile of the user whom has created the task.. |
|title| string | The task title |
|description| string | A longer description of the task |
|comments| comment array | An array of comments related to the thread |

## Portfolio

User's complete portfolio, record as to how much he as earned and other stats regarding his wallet and activity on the website

```
{
    "_id":"d7a44a10-0de3-44ad-9c58-5f3fe8f1c0d3",
    "userID": "7b7997a2-c0d2-4f8c-b27a-6a1d4b5b6310",
    "coinTrack": {
    		"btc": {
    			"quantity": 5,
    			"transactions": ["5a5c4461-cdc9-4144-84f9-fcb278c5c122"]
    		},
    		"ltc": {
    			"quantity": 0,
    			"transactions": []
    		},
    		"eth": {
    			"quantity": 0,
    			"transactions": []
    		}
    }
}
```

<!-- change -->
| Name | Type | Description |
|------|------|-------------|
| _id | string | The comment ID. | 
| poster | User Profile | A profile of the user who made the comment |
| comment | string | The comment that the user made |

## CoinTrack (subdocument; not stored in separate collection)

This subdocument is used to describe the user's coin, that he has bought/owned.

```
{
    		"btc": {
    			"quantity": 5,
    			"transactions": ["5a5c4461-cdc9-4144-84f9-fcb278c5c122"]
    		},
    		"ltc": {
    			"quantity": 0,
    			"transactions": []
    		},
    		"eth": {
    			"quantity": 0,
    			"transactions": []
    		}
    }
```

<!-- change -->
| Name | Type | Description |
|------|------|-------------|
| name | string | The user's name. | 
| hobby | string | A line of text that represents the user's hobby. |
| _id  | string | A globally unique identifier to represent the user |
