# MaterialDayPicker

[![CircleCI](https://circleci.com/gh/gantonious/MaterialDayPicker.svg?style=svg)](https://circleci.com/gh/gantonious/MaterialDayPicker) [![Download](https://api.bintray.com/packages/gantonious/maven/materialdaypicker/images/download.svg)](https://bintray.com/gantonious/maven/materialdaypicker/_latestVersion)

Inspired by the day picker in the builtin Android clock app:

|Normal Usage|Localized Usage|Dark Mode Usage|
|---|---|---|
|![Default Usage](screenshots/default_usage.gif)|![Localized Usage](screenshots/localized_usage.gif)|![Dark Mode Usage](screenshots/dark_mode_usage.gif)|


## Features
- 🎨Customizable theming
- ✅Easy to use API/hooks
- 🌎Fully localized
- 👻Supports dark mode

## What's New: Version 0.6.0 - Handle Device Configuration

**Localization**
- Added device locale support. The day toggles are now rendered in the device language and the first toggle will match the first day of the week for the locale.
- If matching device locale is not desired the locale can be overriden using `materialDayPicker.local = ...`.

**Dark Mode Support**
- Added night mode color assets.

**Configuration Improvements**
- Default colours are now based on the apps `colorPrimary` and `colorPrimaryDark` color values.
- Text color can now be customized for both selected/deselected states by overriding the `daySelectedTextColor` and `dayDeselectedTextColor` colors respectively.

Download the latest version by adding the following to your project's `build.gradle` file:

```groovy
dependencies {
    implementation 'ca.antonious:materialdaypicker:0.6.0'
}
```

## Using MaterialDayPicker in your App

You can just drop the view into your existing xml:

```xml
<ca.antonious.materialdaypicker.MaterialDayPicker
    android:id="@+id/day_picker"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"/>
```

You can get the currently selected days by using:

```kotlin
val selectedDays = materialDayPicker.selectedDays
// returns [MaterialDayPicker.Weekday.TUESDAY, MaterialDayPicker.Weekday.FRIDAY]
```

You can set the selected days by doing:

```kotlin
val daysToSelect = listOf(MaterialDayPicker.Weekday.TUESDAY, MaterialDayPicker.Weekday.FRIDAY)
materialDayPicker.setSelectedDays(daysToSelect)
```

If you want to only allow one day to be selected at a time you can do:

```kotlin
materialDayPicker.selectionMode = SingleSelectionMode.create()
```

If you want to listen to whenever the day selection is changed you can use:

```kotlin
materialDayPicker.setDaySelectionChangedListener { selectedDays ->
    // handle selection change
}
```

If you need to know when a specific day is selected/deselected you can use:


```kotlin
materialDayPicker.setDayPressedListener { weekday, isSelected ->
    // handle weekday selection
}
```

## Customizing MaterialDayPicker for your App

You can override these colors to change how MaterialDayPicker looks. You can also update these values in your night color resources directory to update how MaterialDayPicker looks in dark mode:

```xml
<color name="dayPressed">@color/colorPrimaryDark</color>
<color name="daySelected">@color/colorPrimary</color>
<color name="dayDeselected">#FAFAFA</color>
<color name="daySelectedTextColor">@android:color/white</color>
<color name="dayDeselectedTextColor">@android:color/black</color>
```

If you don't want to use the device's current locale you can override it by doing:

```kotlin
materialDayPicker.locale = Locale.ENGLISH // or any other locale
```

## License

```
MIT License

Copyright (c) 2017 George Antonious

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
