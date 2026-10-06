# How to disable the editor's IsTabStop property in WPF MultiColumn DropDown

This sample demonstrates how to disable the editor's `IsTabStop` property in the [WPF MultiColumn DropDown](https://www.syncfusion.com/wpf-controls/multi-column-dropdown) control.

When you set the `IsTabStop` property of the `MultiColumn DropDown` to `False`, the inner editor element may still receive focus when the user tabs through the UI. To prevent this, you must also disable the `IsTabStop` property for the editor control itself.

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

![MultiColumn DropDown IsTabStop behaviour](SfMultiColumnDropDownControl%20IsTabStop%20Behaviour.gif)

Take a moment to peruse the [WPF MultiColumn DropDown - Editing](https://help.syncfusion.com/wpf/multi-column-dropdown/editing-and-autocomplete) documentation to learn more about editing and autocomplete behavior.

## Requirements to run the sample

* Visual Studio 2019 or later
* .NET Framework or .NET SDK supported by your Syncfusion WPF package
* Syncfusion WPF controls
