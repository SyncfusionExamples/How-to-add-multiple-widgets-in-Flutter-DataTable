# How to add multiple widgets in Flutter DataTable (SfDataGrid)?.

In this article, we will show how to add multiple widgets in [Flutter DataTable](https://www.syncfusion.com/flutter-widgets/flutter-datagrid).

Initialize the [SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) widget with the necessary properties. To display multiple images or widgets in a cell, use the [buildRow](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/buildRow.html) method within the [DataGridSource](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource-class.html). This method allows you to customize the widget displayed in each cell. Inside buildRow, you can add conditional logic for each column or cell to load the appropriate widgets or images.

```dart
@override
  DataGridRowAdapter buildRow(DataGridRow row) {
    return DataGridRowAdapter(
      cells:
          row.getCells().map<Widget>((cell) {
            switch (cell.columnName) {
              case 'id':
                return Container(
                  padding: EdgeInsets.all(8.0),
                  alignment: Alignment.center,
                  child: Row(
                    mainAxisAlignment: MainAxisAlignment.center,
                    children: [
                      Icon(Icons.badge, color: Colors.blue),
                      SizedBox(width: 4),
                      Text(cell.value.toString()),
                    ],
                  ),
                );

              case 'name':
                return Container(
                  padding: EdgeInsets.all(8.0),
                  alignment: Alignment.center,
                  child: Row(
                    mainAxisAlignment: MainAxisAlignment.center,
                    children: [
                      CircleAvatar(
                        radius: 12,
                        backgroundImage: AssetImage(
                          'images/GoldenState.png',
                        ),
                      ),
                      SizedBox(width: 6),
                      Text(cell.value.toString()),
                    ],
                  ),
                );

              case 'designation':
                return Container(
                  padding: EdgeInsets.all(4),
                  alignment: Alignment.center,
                  child: Row(
                    mainAxisAlignment: MainAxisAlignment.center,
                    children: [
                      Image.asset(
                        'images/DenverNuggets.png',
                        width: 20,
                        height: 20,
                      ),
                      SizedBox(width: 4),
                      Image.asset('images/Memphis.png', width: 20, height: 20),
                      SizedBox(width: 4),
                      Image.asset('images/Hornets.png', width: 20, height: 20),
                    ],
                  ),
                );

              case 'salary':
                return Container(
                  padding: EdgeInsets.all(8.0),
                  alignment: Alignment.center,
                  child: Row(
                    mainAxisAlignment: MainAxisAlignment.center,
                    children: [
                      Icon(Icons.monetization_on, color: Colors.green),
                      Text(cell.value.toString()),
                    ],
                  ),
                );

              default:
                return Container(
                  padding: EdgeInsets.all(8.0),
                  alignment: Alignment.center,
                  child: Text(cell.value.toString()),
                );
            }
          }).toList(),
    );
  }
```

You can download this example on [GitHub](https://github.com/SyncfusionExamples/How-to-add-multiple-widgets-in-Flutter-DataTable).