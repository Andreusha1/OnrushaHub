# Onrusha UI Library

Onrusha is a Roblox UI library designed to make creating clean and customizable interfaces easier.

## Installation

Load the library using `loadstring`:

```lua
local library = loadstring(game:HttpGet("https://raw.githubusercontent.com/Andreusha1/OnrushaHub/refs/heads/main/script"))()
```

The library must be executed on the client.

## Creating a Window

Use `library.Create()` to create your interface.

```lua
local Window = library.Create({
    Name = "My Script",
    Subtitle = "My first Onrusha UI",
    Theme = "Midnight",
    Scale = 0.96,
    ToggleKey = Enum.KeyCode.RightShift,
    Draggable = true,
    Blur = true,
    Open = true
})
```

## Creating Tabs

Use `TabCreate()` to add tabs to your window.

```lua
local Main = Window:TabCreate({
    Name = "Main",
    Icon = "home"
})

local Player = Window:TabCreate({
    Name = "Player",
    Icon = "user"
})
```

You can also create sections to organize components inside a tab.

```lua
local Section = Main:SectionCreate({
    Name = "General",
    Side = "Left"
})
```

`Side` can be `"Left"` or `"Right"`.

## Components

All components are created using their respective `Create` methods.

### Toggle

Creates an on/off switch.

```lua
Section:ToggleCreate({
    Name = "Auto Farm",
    Description = "Automatically farms resources",
    Default = false
}):OnChanged(function(value)
    print("Auto Farm:", value)
end)
```

### Button

Creates a clickable button.

```lua
Section:ButtonCreate({
    Name = "Test Button",
    Description = "Click to run an action",
    ButtonText = "Execute"
}):OnClick(function()
    print("Button clicked!")
end)
```

### Slider

Creates a value slider.

```lua
Section:SliderCreate({
    Name = "Walk Speed",
    Min = 16,
    Max = 100,
    Default = 16,
    Step = 1,
    Suffix = " WS"
}):OnChanged(function(value)
    print("Walk Speed:", value)
end)
```

### Dropdown

Allows the user to select an option.

```lua
Section:DropdownCreate({
    Name = "Select Mode",
    Options = {"Easy", "Normal", "Hard"},
    Default = "Normal"
}):OnChanged(function(value)
    print("Selected:", value)
end)
```

### Color Picker

Allows the user to choose a color.

```lua
Section:ColorPickerCreate({
    Name = "UI Color",
    Default = Color3.fromRGB(255, 100, 100)
}):OnChanged(function(color)
    print("Selected color:", color)
end)
```

### Input

Creates a text input field.

```lua
Section:InputCreate({
    Name = "Player Name",
    Placeholder = "Enter a name",
    Default = ""
}):OnChanged(function(value)
    print("Input:", value)
end)
```

## Available Components

Onrusha includes the following components:

| Component | Method |
|---|---|
| Toggle | `ToggleCreate` |
| Button | `ButtonCreate` |
| Slider | `SliderCreate` |
| Slider Toggle | `SliderToggleCreate` |
| Dropdown | `DropdownCreate` |
| Multi Dropdown | `MultiDropdownCreate` |
| Color Picker | `ColorPickerCreate` |
| Color Gradient | `ColorGradientCreate` |
| Input | `InputCreate` |
| Number Input | `NumberInputCreate` |
| Search | `SearchCreate` |
| Keybind | `KeybindCreate` |
| Hotkey | `HotkeyCreate` |
| Checkbox | `CheckboxCreate` |
| Radio Group | `RadioGroupCreate` |
| Multi Toggle | `MultiToggleCreate` |
| Range Slider | `RangeSliderCreate` |
| Progress | `ProgressCreate` |
| Label | `LabelCreate` |
| Paragraph | `ParagraphCreate` |
| Divider | `DividerCreate` |
| Image | `ImageCreate` |
| Image Toggle | `ImageToggleCreate` |
| Image Dropdown | `ImageDropdownCreate` |
| Status | `StatusCreate` |
| Accordion | `AccordionCreate` |
| Keybind List | `KeybindListCreate` |
| Spacer | `SpacerCreate` |
| Custom | `CustomCreate` |

## Component Methods

Components return an object that can be controlled through additional methods.

```lua
local Toggle = Section:ToggleCreate({
    Name = "Example",
    Default = false
})
```

Available methods:

- `:OnChanged(function(value))` — Detects value changes.
- `:OnClick(function())` — Detects clicks.
- `:Get()` — Returns the current value.
- `:Set(value)` — Changes the current value.
- `:SetVisible(boolean)` — Shows or hides the component.
- `:SetDisabled(boolean)` — Enables or disables interaction.
- `:Destroy()` — Removes the component.

## Themes

You can change the interface theme at any time.

```lua
Window:SetTheme("Midnight")
```

Some available themes include:

- Midnight
- Graphite
- Ocean
- Purple
- Emerald
- Crimson
- Rose
- Amber
- Light
- Minimal
- Dracula
- Aurora
- Sakura
- Matcha
- Mocha
- Neon Tokyo
- Carbon
- Terminal
- And many more.

You can also create custom themes using `CreateTheme()`.

## Additional Features

Onrusha also provides several additional functions:

```lua
Window:SetScale(0.9)
Window:SetToggleKey(Enum.KeyCode.RightControl)
Window:SetDraggable(true)
Window:SetPosition(UDim2.fromScale(0.5, 0.5))
Window:Center()
Window:SetUIShadow(true)
```

### Notifications

```lua
Window:Notify({
    Title = "Success",
    Description = "Your action was completed.",
    Type = "Success",
    Duration = 3
})
```

Available notification types: `Info`, `Success`, `Warning`, `Error`.

### Shader Presets

You can apply built-in visual presets:

```lua
Window:ApplyShaderPreset("Cinematic")
```

Available presets include Clean, Cinematic, Vibrant, Dream, Golden Hour, Cyberpunk, Noir, Soft Pastel and Classic Roblox.

### Configurations

Onrusha includes configuration management:

```lua
Window:CreateConfig("MyConfig")
Window:SaveConfig("MyConfig")
Window:LoadConfig("MyConfig")
```

You can also use:

- `Window:ListConfigs()`
- `Window:DeleteConfig(name)`
- `Window:RenameConfig(oldName, newName)`
- `Window:DuplicateConfig(name, copyName)`
- `Window:ExportConfig(name)`
- `Window:ImportConfig(json, name)`

## Complete Example

A simple example combining several components:

```lua
local library = loadstring(game:HttpGet("https://raw.githubusercontent.com/Andreusha1/OnrushaHub/refs/heads/main/script"))()

local Window = library.Create({
    Name = "My Hub",
    Subtitle = "Powered by Onrusha",
    Theme = "Graphite",
    ToggleKey = Enum.KeyCode.RightShift,
    Open = true
})

local Main = Window:TabCreate({
    Name = "Main",
    Icon = "home"
})

local Settings = Main:SectionCreate({
    Name = "Settings",
    Side = "Left"
})

Settings:ToggleCreate({
    Name = "Example Toggle",
    Default = false
}):OnChanged(function(value)
    print("Toggle:", value)
end)

Settings:ButtonCreate({
    Name = "Example Button",
    ButtonText = "Click Me"
}):OnClick(function()
    Window:Notify({
        Title = "Hello",
        Description = "Everything is working!",
        Type = "Success"
    })
end)

Settings:SliderCreate({
    Name = "Speed",
    Min = 1,
    Max = 100,
    Default = 16
}):OnChanged(function(value)
    print("Speed:", value)
end)

Settings:DropdownCreate({
    Name = "Mode",
    Options = {"Normal", "Fast", "Extreme"},
    Default = "Normal"
}):OnChanged(function(value)
    print("Mode:", value)
end)
```

---

**Onrusha UI Library**

GitHub: https://github.com/Andreusha1/OnrushaHub
