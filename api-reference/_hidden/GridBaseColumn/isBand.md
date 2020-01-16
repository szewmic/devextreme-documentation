---
id: GridBaseColumn.isBand
type: Boolean
default: undefined
---
---
##### shortDescription
Specifies whether the column bands other columns or not.

---
Unlike normal columns, band columns do not hold data. Instead, they collect two or more columns under one column header. In most cases, to set up this layout, you can declare the band column using a hierarchical structure. For example, the following code bands three columns under the *"Address"* header.

---
##### jQuery

    <!--JavaScript-->$(function() {
        $("#{widgetName}Container").dx{WidgetName}({
            // ...
            columns: [{
                caption: "Address",
                columns: ["City", "Street", "Apartment"]
            }, {
                // ...
            }]
        });
    });

##### Angular
    
    <!--HTML-->
    <dx-{widget-name} ... >
        <dxi-column caption="Address">
            <dxi-column dataField="City"></dxi-column>
            <dxi-column dataField="Street"></dxi-column>
            <dxi-column dataField="Apartment"></dxi-column>
        </dxi-column>
    </dx-{widget-name}>

    <!--TypeScript-->
    import { Dx{WidgetName}Module } from "devextreme-angular";
    // ...
    export class AppComponent {
        // ...
    }
    @NgModule({
        imports: [
            // ...
            Dx{WidgetName}Module
        ],
        // ...
    })
    
---

If you use the [customizeColumns](/api-reference/10%20UI%20Widgets/dxDataGrid/1%20Configuration/customizeColumns.md '{basewidgetpath}/Configuration/#customizeColumns') option to configure columns, the hierarchical structure cannot be implemented. To band columns in this case, use the **isBand** and [ownerBand](/api-reference/_hidden/GridBaseColumn/ownerBand.md '{basewidgetpath}/Configuration/columns/#ownerBand') options.

---
##### jQuery

    <!--JavaScript-->$(function() {
        $("#{widgetName}Container").dx{WidgetName}({
            // ...
            customizeColumns: function(columns) {
                columns.push({ // Pushes the "Address" band column into the "columns" array
                    caption: "Address",
                    isBand: true
                });
                
                var addressFields = ["City", "Street", "Apartment"];
                for (var i = 0; i < columns.length-1; i++) {
                    if (addressFields.indexOf(columns[i].dataField) > -1) // If the column belongs to "Address",
                        columns[i].ownerBand = columns.length-1; // assigns "Address" as the owner band column
                }
            }
        });
    });

##### Angular
    
    <!--TypeScript-->
    import { Dx{WidgetName}Module } from "devextreme-angular";
    // ...
    export class AppComponent {
        customizeColumns (columns) {
            columns.push({ // Pushes the "Address" band column into the "columns" array
                caption: "Address",
                isBand: true
            });
    
            let addressFields = ["City", "Street", "Apartment"];
            for (let i = 0; i < columns.length - 1; i++) {
                if (addressFields.indexOf(columns[i].dataField) > -1) // If the column belongs to "Address",
                    columns[i].ownerBand = columns.length - 1; // assigns "Address" as the owner band column
            }
        }
    }
    @NgModule({
        imports: [
            // ...
            Dx{WidgetName}Module
        ],
        // ...
    })

    <!--HTML-->
    <dx-{widget-name} ...
        [customizeColumns]="customizeColumns">
    </dx-{widget-name}>
    
---

Band columns can have the following properties only:

- [alignment](/api-reference/_hidden/GridBaseColumn/alignment.md '{basewidgetpath}/Configuration/columns/#alignment')
- [allowHiding](/api-reference/_hidden/GridBaseColumn/allowHiding.md '{basewidgetpath}/Configuration/columns/#allowHiding')
- [allowReordering](/api-reference/_hidden/GridBaseColumn/allowReordering.md '{basewidgetpath}/Configuration/columns/#allowReordering')
- [caption](/api-reference/_hidden/GridBaseColumn/caption.md '{basewidgetpath}/Configuration/columns/#caption')
- [columns](/api-reference/_hidden/GridBaseColumn/columns '{basewidgetpath}/Configuration/columns/columns/')
- [cssClass](/api-reference/_hidden/GridBaseColumn/cssClass.md '{basewidgetpath}/Configuration/columns/#cssClass')
- [fixed](/api-reference/_hidden/GridBaseColumn/fixed.md '{basewidgetpath}/Configuration/columns/#fixed')
- [fixedPosition](/api-reference/_hidden/GridBaseColumn/fixedPosition.md '{basewidgetpath}/Configuration/columns/#fixedPosition')
- [headerCellTemplate](/api-reference/_hidden/GridBaseColumn/headerCellTemplate.md '{basewidgetpath}/Configuration/columns/#headerCellTemplate')
- [name](/api-reference/_hidden/GridBaseColumn/name.md '{basewidgetpath}/Configuration/columns/#name')
- [ownerBand](/api-reference/_hidden/GridBaseColumn/ownerBand.md '{basewidgetpath}/Configuration/columns/#ownerBand')
- [showInColumnChooser](/api-reference/_hidden/GridBaseColumn/showInColumnChooser.md '{basewidgetpath}/Configuration/columns/#showInColumnChooser')
- [visible](/api-reference/_hidden/GridBaseColumn/visible.md '{basewidgetpath}/Configuration/columns/#visible')
- [visibleIndex](/api-reference/_hidden/GridBaseColumn/visibleIndex.md '{basewidgetpath}/Configuration/columns/#visibleIndex')

[note] Band columns cannot nest [command columns](/concepts/05%20Widgets/DataGrid/15%20Columns/10%20Column%20Types/4%20Command%20Columns/00%20Command%20Columns.md '/Documentation/Guide/Widgets/{WidgetName}/Columns/Column_Types/Command_Columns/').

#####See Also#####

- [Band Columns](/concepts/05%20Widgets/DataGrid/15%20Columns/10%20Column%20Types/2%20Band%20Columns.md '/Documentation/Guide/Widgets/{WidgetName}/Columns/Column_Types/Band_Columns/')
<!--/fullDescription-->