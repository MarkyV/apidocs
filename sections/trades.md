# Trade Endpoints

| Endpoint | Description |
| ---- | ---- |
| [GET /v1/accounts/:account_id/trades](https://github.com/oanda/apidocs/blob/master/sections/trades.md#get-v1accountsaccount_idtrades) | Get a list of open trades |
| [POST /v1/accounts/:account_id/trades](https://github.com/oanda/apidocs/blob/master/sections/trades.md#post-v1accountsaccount_idtrades) | Create a open trade |
| [GET /v1/accounts/:account_id/trades/:trade_id](https://github.com/oanda/apidocs/blob/master/sections/trades.md#get-v1accountsaccount_idtradestrade_id) | Get information of an open trade |
| [PUT /v1/accounts/:account_id/trades/:trade_id](https://github.com/oanda/apidocs/blob/master/sections/trades.md#put-v1accountsaccount_idtradestrade_id) | Modify stop loss, take profit, trailing stop an open trade |
| [DELETE /v1/accounts/:account_id/trades/:trade_id](https://github.com/oanda/apidocs/blob/master/sections/trades.md#delete-v1accountsaccount_idtradestrade_id) | Close an open trade |


## GET /v1/accounts/:account_id/trades

#### Request
    http://api-sandbox.oanda.com/v1/accounts/12345/trades?instrument=EUR_USD&maxCount=4

#### Response
    {
      "trades" : [
        { "id" : 12345, "units" : 5, "direction" : "long", "instrument" : "EUR_USD", "time" : 1234567890, "price" : 1.45123, "stopLoss" : 1.2, "takeProfit" : 1.7, "trailingStop" : 10 },
        { "id" : 12344, "units" : 100, "direction" : "short", "instrument" : "EUR_USD", "time" : 1234567891, "price" : 1.45123, "stopLoss" : 1.2, "takeProfit" : 1.7, "trailingStop" : 10 },
        { "id" : 890, "units" : 100, "direction" : "short", "instrument" : "EUR_USD", "time" : 1234567891, "price" : 1.45123, "stopLoss" : 1.2, "takeProfit" : 1.7, "trailingStop" : 10 },
        { "id" : 789, "units" : 100, "direction" : "short", "instrument" : "EUR_USD", "time" : 1234567891, "price" : 1.45123, "stopLoss" : 1.2, "takeProfit" : 1.7, "trailingStop" : 10 }    
      ],
      "nextPage" : "http:\/\/api-sandbox.oanda.com\/v1\/accounts\/1\/trades?maxCount=4&maxTradeId=788"
    }

#### Query Parameters

**Optional**

* **maxTradeId**:  The server will return trades with id less than or equal to this, in descending order (about pagination).
* **maxCount**: Maximum number of open trades to return. Default: 50 Max value: 500
* **instrument**: Restrict open trade for a specific instrument. Default: all
* **tradeIds**: A common separated list of trades to retrieve.

## POST /v1/accounts/:account_id/trades
#### Request
    curl -X POST -d 'instrument=EUR_USD&units=2&direction=short' http://api-sandbox.oanda.com/v1/accounts/12345/trades

#### Response
    {
        "ids" : [207654103, 207654104]   // List of transaction ids resulted from the trade include trades opposition direction that were partially closed
        "units" : 2,
        "direction" : "short",
        "instrument" : "EUR_USD",
        "time" : 1344891136,
        "price" : 1.23325,
        "takeProfit" : 0,
        "stopLoss" : 0,
        "trailingStop" : 0
    }

#### Data Parameters
**Required**

* **instrument**: Instrument to open trade on
* **units**: Number of units to open trade for

**Optional**

* **type** market (default), fillOrKill, ImmediateOrCancel *TODO:what type should be support* 
* **direction** long (default) or short
* **price** User price. All trade request will be executed at server price
* **lowPrice** Minimum execution price
* **highPrice** Maximum execution price
* **stopLoss** Stop Loss value
* **takeProfit** Take Profit value* 
* **trailingStop** Trailing Stop distance in pipettes

[Learn more about order types, stop loss, take profit, and trailing stop](http://fxtrade.oanda.com/learn/intro-to-currency-trading/first-trade/orders)


## GET /v1/accounts/:account_id/trades/:trade_id

#### Request
    http://api-sandbox.oanda.com/v1/accounts/1234/trade/43211

#### Response
    {
      "id" : 43211,             // The ID of the trade
      "units" : 5,                // The number of units in the trade
      "direction" : "long",       // The direction of the trade
      "instrument" : "EUR_USD",   // The symbol of the instrument of the trade
      "time" : 1234567890,        // The time of the trade (seconds since Unix epoch)
      "price" : 1.45123,          // The price the trade was executed at
      "takeProfit" : 1.7,         // The take-profit associated with the trade, if any
      "stopLoss" : 1.4,           // The stop-loss associated with the trade, if any
      "trailingStop" : 10         // The trailing stop associated with the trade, if any
    }



## PUT /v1/accounts/:account_id/trades/:trade_id

#### Request
    curl -X PUT -d 'stopLoss=1.6' http://api-sandbox.oanda.com/v1/trade/43211

#### Response
    {
      "id" : 43212             // The ID of the change trade transaction
    }

#### Parameters
**Optional**

* __stopLoss__: Stop Loss value
* __takeProfit__: Take Profit value
* __trailingStop__: Trailing Stop distance in pipettes




## DELETE /v1/accounts/:account_id/trades/:trade_id

#### Request
    curl -X DELETE http://api-sandbox.aonda.com/v1/accounts/1234/trade/43211

#### Response
    {
      "id" : 54332,               // The ID of the close trade transaction
      "price" : 1.30601           // The pirce trade executed at
      "instrument" : "EUR_USD",   // The symbol of the instrument of the trade
      "profit" :  0.005           // The profit of the trade in dollar (home cuur??)
      "direction" : "short"
    }

#### Parameters
**Optional**

* __price__: Price the client would like to close trade at.  This value will NOT be used by the server

