# LoggingLib

LoggingLib is an Ace3 embeddable logging library designed for addon developpers.

It provides basic logging functions Trace(), Debug(), Info(), Warning(), Error().

It is designed to work with AceConsole-3.0 for print.
It also can take advantage of the DebugLog addon instead of printing to chatframe.

Code example:
```
local addonName, T              = ...
local MyAddon                   = LibStub("AceAddon-3.0"):NewAddon("MyAddon",
                                                                   "AceConsole-3.0",
--@debug@
                                                                   "LoggingLib-0.1"
--@end-debug@
)
local logging_categories_colors = { ["OnInitialize"] = "|r", -- choose whatever color you want
}
--@debug@
local LoggingLib                = LibStub("LoggingLib-0.1")
--@end-debug@

function MyAddon:OnInitialize()
    -- you can surround your debug code with BigWigs mod packager script style tags (see https://github.com/BigWigsMods/packager/wiki)
    --@debug@
    MyAddon:InitializeLogging(addonName,
                              nil, -- use default log level color map. can set your own
                              logging_categories_colors, -- required log categories color mapping (compat with debuglog)
                              LoggingLib.TRACE) -- default log level
    -- log debug with category OnInitialize and some text
    MyAddon:Debug("OnInitialize", "Some Logging text")
    --@end-debug@
end
```
