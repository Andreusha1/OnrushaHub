 
# Onrusha UI

A modern, customizable and responsive UI library for Roblox.

Onrusha provides a collection of UI components, themes, visual effects and configuration tools to help you create clean and professional interfaces.

## Installation

Load the library using:

```lua
local library = loadstring(game:HttpGet("https://raw.githubusercontent.com/Andreusha1/OnrushaHub/refs/heads/main/script"))()
```

## Creating a Window

Create your interface with `library.Create()`:

```lua
local ui = library.Create({
    Name = "Onrusha Hub",
    Subtitle = "My Script",
    Theme = "Matcha",
    Scale = 1,
    ToggleKey = Enum.KeyCode.RightShift,
    Draggable = true,
    MobileSupport = true,
    Blur = true,
    Open = true
})
```

## Tabs and Sections

Organize your interface using tabs and sections.

```lua
local mainTab = ui:TabCreate({
    Name = "Main",
    Icon = "house"
})

local section = mainTab:SectionCreate({
    Name = "Main Settings",
    Side = "Left"
})
```

Sections support `Left` and `Right` positioning.

## Components

Onrusha includes a variety of components:

| Component | Method |
|---|---|
| Toggle | `ToggleCreate()` |
| Button | `ButtonCreate()` |
| Slider | `SliderCreate()` |
| Slider Toggle | `SliderToggleCreate()` |
| Dropdown | `DropdownCreate()` |
| Multi Dropdown | `MultiDropdownCreate()` |
| Color Picker | `ColorPickerCreate()` |
| Color Gradient | `ColorGradientCreate()` |
| Input | `InputCreate()` |
| Number Input | `NumberInputCreate()` |
| Search | `SearchCreate()` |
| Keybind | `KeybindCreate()` |
| Hotkey | `HotkeyCreate()` |
| Checkbox | `CheckboxCreate()` |
| Radio Group | `RadioGroupCreate()` |
| Multi Toggle | `MultiToggleCreate()` |
| Range Slider | `RangeSliderCreate()` |
| Progress | `ProgressCreate()` |
| Label | `LabelCreate()` |
| Paragraph | `ParagraphCreate()` |
| Divider | `DividerCreate()` |
| Image | `ImageCreate()` |
| Image Toggle | `ImageToggleCreate()` |
| Image Dropdown | `ImageDropdownCreate()` |
| Status | `StatusCreate()` |
| Accordion | `AccordionCreate()` |
| Keybind List | `KeybindListCreate()` |
| Spacer | `SpacerCreate()` |
| Custom | `CustomCreate()` |

## Component Examples

### Toggle

```lua
local toggle = section:ToggleCreate({
    Name = "Enable Feature",
    Description = "Enable or disable the feature",
    Default = false
})

toggle:OnChanged(function(value)
    print("Toggle:", value)
end)
```

### Button

```lua
section:ButtonCreate({
    Name = "Example Button",
    ButtonText = "Click Me"
}):OnClick(function()
    print("Button clicked!")
end)
```

### Slider

```lua
local slider = section:SliderCreate({
    Name = "Walk Speed",
    Min = 16,
    Max = 100,
    Default = 16
})

slider:OnChanged(function(value)
    print("Slider:", value)
end)
```

### Dropdown

```lua
local dropdown = section:DropdownCreate({
    Name = "Select Option",
    Options = {"Option 1", "Option 2", "Option 3"},
    Default = "Option 1"
})

dropdown:OnChanged(function(value)
    print("Selected:", value)
end)
```

### Color Picker

```lua
local colorPicker = section:ColorPickerCreate({
    Name = "Select Color",
    Default = Color3.fromRGB(120, 200, 150)
})

colorPicker:OnChanged(function(color)
    print("Selected color:", color)
end)
```

### Input

```lua
local input = section:InputCreate({
    Name = "Player Name",
    Placeholder = "Enter a name..."
})

input:OnChanged(function(value)
    print("Input:", value)
end)
```

## Creating Custom Settings

You can create your own settings page using regular tabs, sections and components.

```lua
local settingsTab = ui:TabCreate({
    Name = "Settings",
    Icon = "settings"
})

local general = settingsTab:SectionCreate({
    Name = "General",
    Side = "Left"
})

local settingsToggle = general:ToggleCreate({
    Name = "Enable Notifications",
    Default = true
})

local settingsSlider = general:SliderCreate({
    Name = "UI Scale",
    Min = 0.5,
    Max = 2,
    Default = 1
})
```

You can connect settings to your own script logic:

```lua
settingsToggle:OnChanged(function(value)
    print("Notifications:", value)
end)

settingsSlider:OnChanged(function(value)
    print("UI Scale:", value)
end)
```

## Component Methods

Components provide methods for controlling their behavior:

| Method | Description |
|---|---|
| `:OnChanged(callback)` | Detect value changes |
| `:OnClick(callback)` | Handle button clicks |
| `:Get()` | Get the current value |
| `:Set(value)` | Change the component value |
| `:SetVisible(boolean)` | Show or hide a component |
| `:SetDisabled(boolean)` | Enable or disable interaction |
| `:Destroy()` | Remove the component |

Example:

```lua
settingsToggle:Set(false)

print(settingsToggle:Get())

settingsToggle:SetVisible(true)
```

## Configurations

Onrusha includes configuration tools for saving, exporting and importing settings.

### Save a Configuration

```lua
local success, err = ui.Configs:Create("MyConfig")

if success then
    print("Configuration saved!")
else
    warn(err)
end
```

### Export a Configuration

```lua
local json, err = ui.Configs:Export("MyConfig")

if json then
    print(json)
end
```

### Import a Configuration

```lua
local success, err = ui.Configs:Import(json, "MyConfig")

if success then
    print("Configuration imported!")
else
    warn(err)
end
```

**Note:** Configurations created with `Configs:Create()` are stored in memory for the current UI session. For permanent storage, your script needs its own storage system.

## Themes

Onrusha supports customizable themes and interface appearance.

You can change the active theme:

```lua
ui:SetTheme("Matcha")
```

You can also create custom themes:

```lua
ui:CreateTheme("MyTheme", {
    -- Custom theme properties
})
```

## Shader Presets

Onrusha includes shader preset tools for managing visual effects.

```lua
local presets = ui:GetShaderPresets()

print(presets)
```

Get the shader controller:

```lua
local shader = ui:GetShader()
```

Apply a preset:

```lua
ui:ApplyShaderPreset("PresetName")
```

## Notifications

Display notifications directly through the library:

```lua
ui:Notify({
    Title = "Onrusha",
    Description = "Settings saved successfully!",
    Type = "Success"
})
```

## Window Controls

You can control the interface programmatically:

```lua
ui:SetToggleKey(Enum.KeyCode.RightShift)
ui:SetScale(1.1)
ui:SetDraggable(true)
ui:SetAnimationsEnabled(true)
ui:SetAnimationSpeed(1)
ui:Center()
```

## Complete Example

```lua
local library = loadstring(game:HttpGet("https://raw.githubusercontent.com/Andreusha1/OnrushaHub/refs/heads/main/script"))()

local ui = library.Create({
    Name = "My Hub",
    Subtitle = "Powered by Onrusha",
    Theme = "Matcha",
    Scale = 1,
    ToggleKey = Enum.KeyCode.RightShift,
    Draggable = true,
    MobileSupport = true,
    Blur = true,
    Open = true
})

local mainTab = ui:TabCreate({
    Name = "Main",
    Icon = "house"
})

local section = mainTab:SectionCreate({
    Name = "Main Features",
    Side = "Left"
})

local toggle = section:ToggleCreate({
    Name = "Enable Feature",
    Default = false
})

toggle:OnChanged(function(value)
    print("Feature enabled:", value)
end)

section:ButtonCreate({
    Name = "Test Notification",
    ButtonText = "Notify"
}):OnClick(function()
    ui:Notify({
        Title = "My Hub",
        Description = "Hello from Onrusha!",
        Type = "Success"
    })
end)
```

---

## Links

- **GitHub:** https://github.com/Andreusha1/OnrushaHub
- **Developer:** Andreusha / Onrusha
- - **Discord:** - https://discord.gg/U3Kmsah8QC
- **Library:** Onrusha UI

**Onrusha UI — Build your interface your way.**
