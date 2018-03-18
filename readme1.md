# StichPunks

* Manank Valnad
* Rohit Keshav
* Mehul Mistry
* Zhiyu Zhou
* Zhang Li

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
| username | string | The user's name. | 
| First_name | string | User's first name. |
| last_name | string | The user's last name. |
| _id  | string | A globally unique identifier to represent the user |
| amount | integer | the final amount in user's account in dollars |


## Transaction

The transaction collection will store all the transactions that have been initiated.


```
{
    "username": "jdog_43", //just to save the fetching time used to fetch only uname from users collection
    "userID": "7b7997a2-c0d2-4f8c-b27a-6a1d4b5b6310"
    "transaction": [
		{	
			"_id":"5a5c4461-cdc9-4144-84f9-fcb278c5c122",
			"timeStamp":"9 May 2017, 23:00:00 GMT"
			"coinName": "eth",
			"action":"buy",
			"quantity": 2,
			"valuePerCoin": 800,
			"stage": "initiated" 	// cancelled, complete
		},
		{	
			"_id":"6sf43sgk-cdc9-4144-84f9-fcb278c5c122",
			"timeStamp":"10 May 2017, 23:00:00 GMT"
			"coinName": "xrp",
			"action":"sell",
			"quantity": 20,
			"valuePerCoin": 0.90,
			"stage": "completed"
		},...]
}
```

<!-- change -->
| Name | Type | Description |
|------|------|-------------|
| username | string | unique username to display on his dashboard | 
| userid | String | A globally unique identifier to represent the user |
| Transaction | list of transactions | A list of all transactions of user |


## A list of transactions (subdocument; not stored in a separate collection)

This subdocument is used to describe the user's profile.

```
{
	"_id":"5a5c4461-cdc9-4144-84f9-fcb278c5c122",
    	"timeStamp":"9 May 2017, 23:00:00 GMT"
	"coinName": "eth",
	"action":"buy",
	"quantity": 2,
	"valuePerCoin": 800,
	"stage": "initiated" 	// cancelled, complete
}
```

| Name | Type | Description |
|------|------|-------------|
| _id | string | unique identifier for each transaction |
| timestamp | string | timestamp for each transaction | 
| coinName | String | Coin used in this transaction |
| action | string | states if user bought or sold in this transaction |
| quantity | integer | quantity of coin user bought/sold in this transaction |
| valuePerCoin | integer | current value of that coin at the time of transaction |
| stage | string | states if transaction has been completed or cancelled or just initiated |



## Portfolio

User's complete portfolio, record as to how much he as earned and other stats regarding his wallet and activity on the website

```
{
    "userID": "7b7997a2-c0d2-4f8c-b27a-6a1d4b5b6310",
    "coinTrack": {
    		"btc": {
    			"quantity": 5,
    			"transactions": ["5a5c4461-cdc9-4144-84f9-fcb278c5c122"]
    		},
    		"ltc": {
    			"quantity": 3,
    			"transactions": ["6sf43sgk-cdc9-4144-84f9-fcb278c5c122", "8ehs234b-cdc9-4144-84f9-fcb278c5c122"]
    		},...
    }
}
```

<!-- change -->
| Name | Type | Description |
|------|------|-------------|
| userID | string | A globally unique identifier to represent the user | 
| cointrack | object of objects | An object of coin tracking objects |

## CoinTrack (subdocument; not stored in separate collection)

This subdocument is used to describe the user's coin, that he has bought/owned.

```
{
	"btc": {
		"quantity": 5,
		"transactions": ["5a5c4461-cdc9-4144-84f9-fcb278c5c122"]
	},
	"ltc": {
		"quantity": 3,
		"transactions": ["6sf43sgk-cdc9-4144-84f9-fcb278c5c122", "8ehs234b-cdc9-4144-84f9-fcb278c5c122"]
	},...
}
```

<!-- change -->
| Name | Type | Description |
|------|------|-------------|
| coin_name | object | object of this coin's detailed transaction | 
| quantity | integer | quantity of the coin used in transaction |
| transaction  | List of strings | A list of string containing all transaction happened with this user for this coin |
