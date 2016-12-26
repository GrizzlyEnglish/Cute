# Cute
Micro unit testing for Love2d

## What?

Cute lets you [unit test](https://en.wikipedia.org/wiki/Unit_testing) your game code and provides a **minimal** GUI for seeing the results in game.

You can also run the tests headlessly on a CI server if that's your jam.

## Installation

- Download `cute.lua` and add it to your your source code.
- Write some tests:
```lua
cute = require("tests.cute") -- remember to use the path you downloaded cute to

verify("1 + 1 = 2", 1 + 1).is(2) -- passes

verify("All equal 7", {7, 7, 7}).all(function (v) return (v == 7) end) -- passes

local foo = "zap"
verify("foo is bar", foo).is("bar") -- fails
```
- Add `cute.go(args)` to love.load in your main.lua file (remember to require cute and your tests)
- Optionaly add `cute.draw()` and `cute.keys(key)` to your love.draw and love.keypressed functions (also in main.lua)
- Run your game with `path/to/love game_directory --cute` or `path/to/love game_directory --cute-headless`

## GUI Mode

By default GUI mode has the following controls:
- `h` hide the test results
- `j` scroll results up
- `k` scroll results down

The controls can be remapped with `cute.setKeys("hideKey","upKey","downKey")`
The position of the results can be set with `cute.setResultsPosition(x,y)`

## Matchers

Cute currently has two matchers:
- `verify("something", a).is(b)` will test if a == b
- `verify("all of something", t).all(function (v) ... end)` will run the supplied predicate against all the values of v in the table t. The test will fail if the predicate returns false for any values.
- ... more to come as I need them

## Future features

Let me know what you'd like or raise a pull request :)