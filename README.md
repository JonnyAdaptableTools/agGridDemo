# agGridDemo
Very basic one file demo showing how to integrate Adaptable Blotter and ag-Grid.  Based on ag-Grid's own starter demo (https://www.ag-grid.com/javascript-getting-started/)

All that is needed is to instantiate ag-Grid and pass the gridOptions into the Adatpable Blotter.

Note its your responsiblity to download ag-Grid - and if using the Enterprise version please ensure you have a licence!

The entire code for the demo is here:

<!DOCTYPE html>
<html>

<head>
    <!-- Some ag-Grid files - its responsibility of dev to get these: we dont provide-->
    <script src="https://unpkg.com/ag-grid-enterprise/dist/ag-grid-enterprise.min.noStyle.js"></script>
    <link rel="stylesheet" href="https://unpkg.com/ag-grid/dist/styles/ag-grid.css">
    <link rel="stylesheet" href="https://unpkg.com/ag-grid/dist/styles/ag-theme-balham.css">

    <!-- the adaptable blotter file -->
    <script src="node_modules/adaptableblotter/dist/adaptableblotteraggrid-bundle.min.js"></script>

    <!-- adaptable blotter stylesheet - will provide this as downloadable pacakge very soon -->
    <link rel="stylesheet" href="bootstrap/css/bootstrap.min.css">

</head>

<body>
    <!-- div for the adaptable blotter -->
    <div id="adaptableBlotter" style="margin:0px"></div>

    <!-- div for the ag-Grid -->
    <div id="grid" style="height: 600px;width:500px;" class="ag-theme-balham"></div>

    <script type="text/javascript" charset="utf-8">
        // specify the columns
        var columnDefs = [
            { headerName: "Make", field: "make" },
            { headerName: "Model", field: "model" },
            { headerName: "Price", field: "price" }
        ];

        // specify the data
        var rowData = [
            { make: "Toyota", model: "Celica", price: 35000 },
            { make: "Ford", model: "Mondeo", price: 32000 },
            { make: "Porsche", model: "Boxter", price: 72000 }
        ];

        // let the grid know which columns and what data to use
        var gridOptions = {
            columnDefs: columnDefs,
            rowData: rowData,
            enableSorting: true
        };

        // create the grid passing in the div to use together with the columns & data we want to use
        new agGrid.Grid(document.querySelector('#grid'), gridOptions);

        // instantiate the Adaptable Blotter, passing in the AdaptableBlotterOptions
        // this has minimum props - just pk and gridOptions
        adaptableblotter = new adaptableblotteraggrid.AdaptableBlotter(
            {
                primaryKey: "make",
                vendorGrid: gridOptions,
            }
        );

    </script>
</body>

</html>
