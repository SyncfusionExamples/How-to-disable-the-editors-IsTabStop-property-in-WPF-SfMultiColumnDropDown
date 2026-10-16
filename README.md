# How to disable the editor's IsTabStop property in WPF MultiColumn DropDown

This sample demonstrates how to disable the editor's `IsTabStop` property in the [WPF MultiColumn DropDown](https://www.syncfusion.com/wpf-controls/multi-column-dropdown) control.

## Overview

When you set the `IsTabStop` property of the `MultiColumn DropDown` to `False`, the inner editor element may still receive focus when the user tabs through the UI. To prevent this, you must also disable the editor's `IsTabStop` property after the control is loaded so that tab navigation skips the inner editor. This sample shows how to locate the inner editor (a `TextBox`) and set its `IsTabStop` to `False` in the control's `Loaded` event.

## XAML

```xml
<syncfusion:SfMultiColumnDropDownControl x:Name="sfMultiColumn"
                                         IsTabStop="False"
                                         Grid.Column="0"
                                         ItemsSource="{Binding Orders}"
                                         DisplayMember="OrderID"
                                         Width="175"
                                         Height="30"
                                         SelectedIndex="2"
                                         Loaded="sfMultiColumn_Loaded"/>
```

## C#

```csharp
private void sfMultiColumn_Loaded(object sender, RoutedEventArgs e)
{
    TextBox textBox = (TextBox)GridUtil.FindDescendantChildByType(sfMultiColumn, typeof(TextBox));
    if (textBox != null)
        textBox.IsTabStop = false;
}
```

## Solution

The code above demonstrates the recommended approach: keep the drop-down control itself non-tab-stop by setting `IsTabStop="False"` on the control, and also find and set the inner editor's `IsTabStop` to `False` once the control is loaded. This ensures both the control and its editor are skipped during keyboard tab navigation.

![MultiColumn DropDown IsTabStop behaviour](SfMultiColumnDropDownControl%20IsTabStop%20Behaviour.gif)

Take a moment to peruse the [WPF MultiColumn DropDown - Editing](https://help.syncfusion.com/wpf/multi-column-dropdown/editing-and-autocomplete) documentation to learn more about editing and autocomplete behavior for this control.

## Requirements to run the sample

* Visual Studio 2019 or later
* .NET Framework or .NET SDK supported by your Syncfusion WPF package
* Syncfusion WPF controls
