:chart: All content on this page is related to [Trading Terminal](Trading-Terminal) only.

Broker API is a key component that enables live trading. Its main purpose is to connect our charts with your trading logic. In terms of `JS`, it is an `object` which is expected to expose the specific interface. Here is a list of API's **methods** that Terminal is expected to have.

## Required Methods

### constructor(host)

The constructor of the Broker API usually takes [Trading Host](Trading-Host.md).

### positions : Promise<Position[]>

This method is called by the Trading Terminal to request [positions](Trading-Objects-and-Constants.md#position).

### orders : Promise<Order[]>

This method is called by the Trading Terminal to request [orders](Trading-Objects-and-Constants.md#order).

### executions(symbol) : Promise<Execution[]>

This method is called by the Trading Terminal to request [executions](Trading-Objects-and-Constants.md#execution).

### trades : Promise<Trade[]>

This method is called by the Trading Terminal to request [trades](Trading-Objects-and-Constants.md#trade) (individual positions).

### chartContextMenuActions(e)

- `e` is a context object passed by a browser

Chart can have a sub-menu `Trading` in the context menu. It returns the list of items in a sub-menu. The format is the same as in `buttonDropdownItems`.

### connectionStatus()

You don't need to return values other than `1` typically since the broker is already connected when you create the widget. You can use it if you want to display a spinner in the bottom panel while the data is being loaded.
Possible return values are:

```javascript
ConnectionStatus.Connected = 1
ConnectionStatus.Connecting = 2
ConnectionStatus.Disconnected = 3
ConnectionStatus.Error = 4
```

### isTradable(symbol): Promise<boolean | IsTradableResult>

This function is required for the Floating Trading Panel. The ability to trade via the panel depends on the result of this function: `true` or `false`. You don't need to implement this method if all symbols can be traded.

If you want to show a custom message with the reason why the symbol cannot be traded then you can return an object `IsTradableResult`. It has only two keys: tradable (`true` or `false`) and reason (`string`).

### accountManagerInfo()

This function should return the information that will be used to build an account manager.
See [Account Manager](Account-Manager.md) for more information.

### showOrderDialog([order](Trading-Objects-and-Constants.md#order))

This function is requested by the chart when a user creates or modifies an order.

You have the ability to use your own dialog and manage it as you see fit.

### placeOrder([order](Trading-Objects-and-Constants#order.md))

Method is requested when a user wants to place an order. Order is pre-filled with partial or complete information.

### modifyOrder([order](Trading-Objects-and-Constants.md#order))

1. `order` is an order object to modify

Method is requested when a user wants to modify an existing order.

### cancelOrder(orderId)

This method is requested to cancel a single order with a given `id`.

If `silently` is `true` no dialogs should be shown.

### cancelOrders(symbol, side, ordersIds, silently)

1. `symbol` - symbol string
1. `side`: [Side constant](Trading-Objects-and-Constants.md#side) or `undefined`
1. `ordersIds` - ids already collected by `symbol` and `side`

If `silently` is `true` no dialogs should be shown.

This method is requested to cancel multiple orders for a `symbol` and `side`.

### editPositionBrackets(positionId, [brackets](Trading-Objects-and-Constants.md#brackets))

1. `positionId` is an ID of an existing position to be modified
1. `brackets` - new [brackets](Trading-Objects-and-Constants.md#brackets) (optional).

This method is requested if `supportPositionBrackets` configuration flag is on. It shows a dialog that enables take profit and stop loss editing.

### closePosition(positionId)

This method is requested if `supportClosePosition` configuration flag is on. It allows to close the position by id.

### reversePosition(positionId)

This method is requested if `supportReversePosition` configuration flag is on. It allows to reverse the position by id.

### editTradeBrackets(tradeId, [brackets](Trading-Objects-and-Constants.md#brackets))

1. `tradeId` is ID of existing trade to be modified
1. `brackets` - new [brackets](Trading-Objects-and-Constants.md#brackets) (optional).

This method is requested if `supportTradeBrackets` configuration flag is on. It displays a dialog that enables take profit and stop loss editing.

### closeTrade(tradeId)

This method is requested if `supportCloseTrade` configuration flag is on. It allows to close the trade by id.

### symbolInfo(symbol) : Deferred (or Promise)

1. `symbol` - symbol string

This method is requested by the internal Order Dialog, DOM panel and floating trading panel to get symbol information.

The result is an object with the following data:

- `qty` - object with fields `min`, `max` and `step` that specifies Quantity, field step and boundaries.
- `pipSize` - size of 1 pip (e.g., 0.0001 for EURUSD).
- `pipValue` - value of 1 pip for the instrument in the account currency.
- `minTick` - minimal price change (e.g., 0.00001 for EURUSD). Used for price fields.
- `description` - a description to be displayed in the dialog.
- `type` - instrument type, only `forex` matters - it enables negative pips. You can check that in the order dialog.
- `domVolumePrecision` - number of decimal places of DOM asks/bids volume (optional, 0 by default).
- `marginRate` - the margin requirement for the instrument. A 3% margin rate should be represented as 0.03.

### accountInfo() : Deferred (or Promise)

This method is requested by the internal Order Dialog to get the account information.
It should return only one field for now:

1. currencySign: string - which is a sign of account currency

Once this method is called the broker should stop providing profit/loss.

### subscribeEquity()

The method should be implemented if you use the standard order dialog and support stop loss. Equity is used to calculate Risk in Percent.

Once this method is called the broker should provide equity (Balance + P/L) updates via [equityUpdate](Trading-Host.md#equityupdateequity) method.

### unsubscribeEquity()

The method should be implemented if you use the standard order dialog and support stop loss.

Once this method is called the broker should stop providing equity updates.

### subscribeMarginAvailable()

The method should be implemented if you use the standard order dialog and want to show the margin meter.

Once this method is called the broker should provide margin available updates via [marginAvailableUpdate](Trading-Host#marginavailableupdatemarginavailable) method.

### unsubscribeMarginAvailable()

The method should be implemented if you use the standard order dialog want to show the margin meter.

Once this method is called the broker should stop providing margin available updates.

### subscribePipValue()

The method should be implemented if you use a standard order dialog. `pipValues` is displayed in the Order info and it is used to calculate the Trade Value and risks. If this method is not implemented then `pipValue` from the `symbolInfo` is used in the order panel/dialog.

Once this method is called the broker should provide `pipValue` updates via [pipValueUpdate](Trading-Host.md#pipvalueupdatesymbol-pipValues) method.

### unsubscribePipValue()

The method should be implemented if you use a standard order dialog and implement `subscribePipValue`.

Once this method is called the broker should stop providing `pipValue` updates.

## See Also

- [How to connect](Widget-Constructor.md#brokerfactory) your trading controller to the chart
- [Trading Host](Trading-Host.md)
