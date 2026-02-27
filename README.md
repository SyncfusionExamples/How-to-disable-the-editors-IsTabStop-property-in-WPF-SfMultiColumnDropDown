# How-to-disable-the-editor-s-IsTabStop-property-in-WPF-SfMultiColumnDropDown

In [WPF MultiColumnDropDown](https://www.syncfusion.com/wpf-controls/multi-column-dropdown) (SfMultiColumnDropDown), when you set IsTabStop to false for the SfMultiColumnDropDownControl, the editor control’s (TextBox) IsTabStop property remains active and continues to receive focus during tab navigation.

To prevent the editor control from receiving focus, you need disable the IsTabStop property for both the editor control and the SfMultiColumnDropDownControl. You can access the editor control (TextBox) in the Loaded event of the SfMultiColumnDropDownControl and set its IsTabStop property to false.

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

![SfMultiColumnDropDownControl IsTabStop Behaviour](SfMultiColumnDropDownControl%20IsTabStop%20Behaviour.gif)

Take a moment to peruse the [WPF MultiColumnDropDown - Editing](https://help.syncfusion.com/wpf/multi-column-dropdown/editing-and-autocomplete) documentation, to learn more about editing and autocomplete with examples.