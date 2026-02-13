# How to skip a selection for any specific index or based on selected items count in xamarin.forms listview?

This example demonstrates how to skip a selection for any specific index or based on selected items count in xamarin.forms listview.

## Sample

```xaml
<synfusion:SfListView x:Name="listView"
                    ItemSize="70" 
                    ItemsSource="{Binding ContactsInfo}"
                    SelectionMode="Multiple"
                    SelectionChanging="listView_SelectionChanging">
    <synfusion:SfListView.ItemTemplate>
        <DataTemplate>
            <ViewCell>
                <ViewCell.View>
                    <code>
                    . . .
                    . . .
                    <code>
                </ViewCell.View>
            </ViewCell>
        </DataTemplate>
    </synfusion:SfListView.ItemTemplate>
</synfusion:SfListView>

Code behind:
private void listView_SelectionChanging(object sender, Syncfusion.ListView.XForms.ItemSelectionChangingEventArgs e)
{
    var addedItemCount = e.AddedItems.Count;
    if (addedItemCount == 0)
        return;

    var items = e.AddedItems;
    var index = listView.DataSource.DisplayItems.IndexOf(items[0]);
    if (index == 1)
        e.Cancel = true;     //Selection cancelled for 1st item

    if (listView.SelectedItems.Count>=3 && addedItemCount != 0)
    {
        e.Cancel = true;
        DisplayAlert("Message", "You can select only 3 items.Can you please deselect any one item", "Ok");
    }
}
```

See [How to skip a selection for any specific index or based on selected items count in xamarin.forms listview](https://www.syncfusion.com/kb/10011/how-to-skip-a-selection-for-any-specific-index-or-based-on-selected-items-count-in-xamarin-forms) for more details.

## Requirements to run the demo

* [Visual Studio 2017](https://visualstudio.microsoft.com/downloads/) or [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/)
* Xamarin add-ons for Visual Studio (available via the Visual Studio installer).

## Troubleshooting

### Path too long exception

If you are facing path too long exception when building this example project, close Visual Studio and rename the repository to short and build the project.
