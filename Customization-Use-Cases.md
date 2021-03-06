Charting Library allows you to customize the appearance, the way it displays data, default properties and lots of other parameters.

There are client-side and server-side customizations. Some of them are made through the constructor, others are made using widget/chart methods.

We've gathered the most used customizations along with the links to their descriptions for your convenience.

#### Default instrument and resolution

Change the default symbol (instrument) and resolution (time interval).

Minimum supported resolution is 1 second.

[documentation](Widget-Constructor.md#symbol-interval)

#### Default visible range (timeframe)

Change time range of bars for the default resolution

[documentation](Widget-Constructor.md#timeframe)

#### Default visible range for resolutions

Change time range of bars when the resolution is changed by the user. A sample is available here:

[documentation](Chart-Methods#onintervalchanged)

#### Initial timezone

You can set the default timezone. It can be changed by the user in the menu.

[documentation](Widget-Constructor.md#timezone)

#### Chart size

You can add the chart as a web page element or use a fullscreen mode.

[Width and Height](Widget-Constructor.md#width-height)

[Fullscreen](Widget-Constructor.md#fullscreen)

[Autosize](Widget-Constructor.md#autosize)

#### Chart colors

Customize the colors of the chart so that it matches your site design.

1. Toolbar color - [documentation](Widget-Constructor.md#toolbar_bg)
1. Chart color - [documentation](Widget-Constructor.md#overrides)

#### Indicators

1. Limit the amount of indicators per chart layout - [documentation](Widget-Constructor.md#study_count_limit)
1. Limit the number of indicators that can be displayed and added - [documentation](Widget-Constructor.md#studies_access)
1. Add your own indicators that are calculated on the server - [documentation](Creating-Custom-Studies.md)
1. Change the default properties of indicators - [documentation](Widget-Constructor.md#studies_overrides)
1. Change the default properties on the fly - [documentation](Widget-Methods.md#applystudiesoverridesoverrides)

#### Drawings

1. Limit the number of drawings that can be displayed and added - [documentation](Widget-Constructor.md#drawings_access)
1. Change the default properties of drawings - [documentation](Widget-Constructor.md#overrides)
1. Change the default properties on the fly - [documentation](Widget-Methods.md#applyoverridesoverrides)

#### Language

More than 20 translated versions of the Charting Library are available to you.

[documentation](Widget-Constructor.md#locale)

Note that you select the language when creating the chart. You'd have to recreate the chart if you wish to change the language.

#### Formatting numbers, dates

1. Change the decimal sign of numbers - [documentation](Widget-Constructor.md#numeric_formatting)
1. Set custom formatters for time and data - [documentation](Widget-Constructor.md#customformatters)
1. Prices are formatted according to the symbol information - [documentation](Symbology.md#minmov-pricescale-minmove2-fractional)

#### Default properties of a chart

You can change any available properties in the properties dialog.

1. Initially - [documentation](Widget-Constructor.md#overrides)
1. On the fly - [documentation](Widget-Methods.md#applyoverridesoverrides)

#### Server for snapshots

TradingView allows you to save snapshots to its servers. You can change this if you wish.

[documentation](Widget-Constructor.md#snapshot_url)

#### Show/hide chart elements

Certain chart elements (toolbars, buttons, other controls) can be hidden if you don't need them.

1. Most of the chart elements can be shown/hidden by using [Featuresets](Featuresets)
1. You can add your own CSS - [documentation](Widget-Constructor.md#custom_css_url)

#### Timeframes at the bottom of the chart

Timeframe is a time period of bars. It's a preferred resolution to display the period. The list can be customized.

[documentation](Widget-Constructor.md#time_frames)

#### Initial list of favorite intervals / chart styles

You can select the intervals and chart styles that will be shown in the top toolbar by default. A user can change it if `items_favoriting` is enabled in the [Featuresets](Featuresets).

[documentation](Widget-Constructor.md#favorites)

#### Resolutions that are displayed in the menu

1. The complete list of resolutions is provided in the configuration of the datafeed - [documentation](JS-Api.md#supported_resolutions)
1. Resolutions are enabled or disabled in the list basing on the symbol information - [documentation](Symbology.md#supported_resolutions)
1. Initial list of favorite resolutions can be adjusted - [documentation](Widget-Constructor.md#favorites)

#### Volume indicator

Volume is added by default if the financial instrument supports it ([documentation](Symbology.md#has_no_volume)).
This behavior can be disabled using [documentation](Featuresets.md).

#### Context menu

You can add new elements to the context menu or hide the existing items.

[documentation](Widget-Methods.md#oncontextmenucallback)

#### Custom buttons on the toolbar

You can add your own buttons to the top toolbar.

[documentation](Widget-Methods.md#createbuttonoptions)

#### :chart: Watchlist

You can select the default symbols for the watchlist and set them to read-only if needed.

[documentation](Widget-Constructor.md.md#widgetbar)

#### :chart: News feed

You can attach to any RSS feed and even select the feed depending on the type of the financial instrument.

[documentation](Widget-Constructor.md.md#rss_news_feed)
