# Sweeper.spoon
Hammerspoon - Automatically hide apps that are out of focus.

This uses a hs.window.filter to detect windows that have gone out of focus. Then, if they are configured to be "swept" in the apps config, they will be automatically hidden if they remain out of focus after sweepCheckInterval (default 15 seconds).

# Installation

## Automated

Sweeper can be automatically installed from my [Spoon Repository](https://github.com/adammillerio/Spoons) via [SpoonInstall](https://www.hammerspoon.org/Spoons/SpoonInstall.html). See the repository README or the SpoonInstall docs for more information.

Example `init.lua` configuration which configures `SpoonInstall` and uses it to install and start Sweeper:

```lua
hs.loadSpoon("SpoonInstall")

spoon.SpoonInstall.repos.adammillerio = {
    url = "https://github.com/adammillerio/Spoons",
    desc = "adammillerio Personal Spoon repository",
    branch = "main"
}


spoon.SpoonInstall:andUse("Sweeper", {
    repo = "adammillerio",
    start = true,
    config = {
        apps = {
            ["Calendar"] = {sweep = true},
            ["Reminders"] = {sweep = true, sweepCheckInterval = 30},
        },
        sweepCheckInterval = 15
    }
}
```

This will configure Calendar windows to be swept 15 seconds after they lose focus. Reminders, on the other hand, will be swept 30 seconds after losing focus instead.

## Manual

Download the latest Sweeper release from [here.](https://github.com/adammillerio/Spoons/raw/main/Spoons/Sweeper.spoon.zip)

Unzip and either double click to load the Spoon or place the contents manually in `~/.hammerspoon/Spoons`

Then load the Spoon in `~/.hammerspoon/init.lua`:

```lua
hs.loadSpoon("Sweeper")

hs.spoons.use("Sweeper", {
    start = true,
    config = {
        apps = {
            ["Calendar"] = {sweep = true},
            ["Reminders"] = {sweep = true, sweepCheckInterval = 30},
        },
        sweepCheckInterval = 15
    }
}
```

# Usage

Refer to the [hosted documentation](https://adammiller.io/Spoons/Sweeper.html) for information on usage.
