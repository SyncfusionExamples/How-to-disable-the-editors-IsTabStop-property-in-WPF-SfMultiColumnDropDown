# How-to-disable-the-editor-s-IsTabStop-property-in-WPF-SfMultiColumnDropDown

In [WPF MultiColumnDropDown](https://www.syncfusion.com/wpf-controls/multi-column-dropdown) (SfMultiColumnDropDown), when you set IsTabStop to false for the SfMultiColumnDropDownControl, the editor[...]

## Example

**XAML**
```
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

**C#**
```
private void sfMultiColumn_Loaded(object sender, RoutedEventArgs e)
{
    TextBox textBox = (TextBox)GridUtil.FindDescendantChildByType(sfMultiColumn, typeof(TextBox));
    textBox.IsTabStop = false;
}
```

## Output

![SfMultiColumnDropDownControl IsTabStop Behaviour](SfMultiColumnDropDownControl%20IsTabStop%20Behaviour.gif)

Take a moment to peruse the [WPF MultiColumnDropDown - Editing](https://help.syncfusion.com/wpf/multi-column-dropdown/editing-and-autocomplete) documentation to learn more about editing and autoco[...]

---

## Purpose

This sample shows how to ensure that the embedded editor (TextBox) inside a Syncfusion SfMultiColumnDropDownControl does not receive focus when tabbing through controls by disabling the IsTabStop [...]

## Prerequisites

- Visual Studio 2019 or later (Visual Studio 2022 recommended)
- .NET Framework 4.6.1 or later, or .NET Core / .NET 5+ (choose the target that matches your sample project)
- Syncfusion WPF controls installed (you can add Syncfusion WPF NuGet packages or reference installed assemblies)
- A Syncfusion license if you are using licensed Syncfusion binaries (refer to Syncfusion's licensing documentation)

## Supported versions

This guidance applies to Syncfusion WPF MultiColumnDropDown controls available in recent releases (2019 and later). API names used in this sample (IsTabStop, control template structure) have been [...]

## How it works (technical details)

The SfMultiColumnDropDownControl control template contains an inner editor control (a TextBox) that can still participate in the tab order even after you set IsTabStop on the outer control to fals[...]

Tips:
- If the control template changes in future Syncfusion versions, the search helper may need to locate the element by name or use Template.FindName on the control's template.
- Always null-check the found element before setting properties to avoid NullReferenceException.

## Usage

1. Open the sample WPF project in Visual Studio.
2. Restore NuGet packages and ensure Syncfusion WPF assemblies are referenced.
3. Set the project's target framework to the version you prefer (e.g., .NET Framework 4.8 or .NET 6 if using WPF on .NET Core/5+).
4. Build and run the sample.
5. Press Tab in the running sample to verify that the SfMultiColumnDropDownControl and its inner editor are not focused.

## Troubleshooting

- Inner TextBox not found: The control template may have changed. Use Visual Studio Live Visual Tree or Snoop to inspect the runtime visual tree and locate the editor element.
- Loaded handler not firing: Make sure the XAML includes Loaded="sfMultiColumn_Loaded" on the control and that the event handler signature matches the sample.
- NullReferenceException: Always check the returned element from the visual-tree helper before using it.

## Example visual-tree helper (simplified)

```
public static class VisualTreeHelperExtensions
{
    public static T FindDescendant<T>(DependencyObject root) where T : DependencyObject
    {
        if (root == null) return null;
        int count = VisualTreeHelper.GetChildrenCount(root);
        for (int i = 0; i < count; i++)
        {
            var child = VisualTreeHelper.GetChild(root, i);
            if (child is T t) return t;
            var found = FindDescendant<T>(child);
            if (found != null) return found;
        }
        return null;
    }
}
```

You can use the above helper as an alternative to GridUtil.FindDescendantChildByType if that utility is not available in your project.

## Contributing

Contributions are welcome. Please open an issue or a pull request with a clear description of your changes. If you add code samples or alter the project structure, update this README accordingly.

---

If you want, I can also add a runnable sample (MainWindow.xaml and MainWindow.xaml.cs) targeting a specific framework (for example .NET Framework 4.8 or .NET 6/7 WPF). Tell me which target you pr[...]
