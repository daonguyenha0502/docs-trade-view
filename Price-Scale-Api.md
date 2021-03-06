## Price Scale API

### getMode()

Returns current [mode](#pricescalemode) of the price scale.

### setMode(newMode)

1. `newMode` - new [mode](#pricescalemode) for the price scale

Changes current mode of the price scale.

### isInverted()

*Since version 1.15.*

Returns whether the price scale is inverted or not.

### setInverted(isInverted)

*Since version 1.15.*

1. `isInverted` - new inverted state for the price scale

Changes current inverted state of the price scale.

## Primitive Types

### PriceScaleMode

Available modes price scale can operate in:

* `0` - normal mode of the price scale
* `1` - logarithmic mode of the price scale
* `2` - percentage mode of the price scale
* `3` - indexed to 100 mode of the price scale
