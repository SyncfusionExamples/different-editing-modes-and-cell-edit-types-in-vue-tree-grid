<template>
  <ejs-treegrid :dataSource="data"
    childMapping="subtasks"
    :treeColumnIndex="1"
    :editSettings="editOptions"
    :toolbar="toolbarSettings"
    :allowPaging="true">
    <e-columns>
      <e-column field="taskID" :isPrimaryKey="true" headerText="Task ID" width="70" textAlign="Right"></e-column>
      <e-column field='taskName' headerText='Task Name' width='200'></e-column>
      <e-column field='startDate' headerText='Start Date' width='110'
         format="yMd" textAlign='Right' editType="datepickeredit"
         :edit="dateTimeParams"></e-column>
      <e-column field='duration' headerText='Duration' width='80' textAlign='Right' editType="numericedit"></e-column>
      <e-column field='priority' headerText='Priority' width='90' editType="dropdownedit"></e-column>
      <e-column field='approved' headerText='Approved' width='90' editType="booleanedit" displayAsCheckBox="true"></e-column>
      <e-column headerText="Manage Records" :commands="commands" width="100"></e-column>
    </e-columns>
  </ejs-treegrid>
</template>

<script>
import {TreeGridComponent, ColumnsDirective, ColumnDirective, Page, Edit, Toolbar, CommandColumn} from '@syncfusion/ej2-vue-treegrid';
import {sampleData} from './data.js';
export default {
  name: 'App',
  components: {
    'ejs-treegrid': TreeGridComponent,
    'e-columns': ColumnsDirective,
    'e-column': ColumnDirective
  },
  data:()=>{
    return{
      data: sampleData,
      editOptions: {allowAdding:true, allowEditing:true, allowDeleting:true, mode:"Row"},
      toolbarSettings: ["Add", "Delete", "Update", "Cancel", "Edit"],
      dateTimeParams: {params:{format:"d-MMM-y hh:mm a"}},
      commands: [
        { type: 'Edit', buttonOption: { iconCss: ' e-icons e-edit', cssClass: 'e-flat' } },
        { type: 'Delete', buttonOption: { iconCss: 'e-icons e-delete', cssClass: 'e-flat' } },
        { type: 'Save', buttonOption: { iconCss: 'e-icons e-update', cssClass: 'e-flat' } },
        { type: 'Cancel', buttonOption: { iconCss: 'e-icons e-cancel-icon', cssClass: 'e-flat' } }
      ]
    }
  },
  provide:{
    treegrid: [Page, Edit, Toolbar, CommandColumn]
  }
}
</script>

<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-calendars/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-dropdowns/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-grids/styles/material.css";
  @import "../node_modules/@syncfusion/ej2-vue-treegrid/styles/material.css";

  .btn{
    margin: 1%;
  }
</style>
