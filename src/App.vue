<template>
    <div>
          <div class="menu">
            <button @click="ChangeCol">Tùy chỉnh</button>
          </div>
          <div id='container' style="width:calc(100% - 250px);">
            <div class="control-section">
              <!--  DashboardLayout element declaration -->
              <ejs-listbox id="listbox1" :itemTemplate= "itemtemplate1"  scope="combined-dashboard-layout"></ejs-listbox>
                <ejs-dashboardlayout id='defaultLayout' :cellSpacing="spacing" :dragStart="dragStartDashboard" :allowFloating="false"  ref="dashboard" :columns="12" :allowDragging ='allowDragging'>
                    <div id="one" class="e-panel" data-row="0" data-col="0" data-sizeX="2" data-sizeY="2">
                        <div class="e-panel-container">
                            <div class="text-align">
                                <div>1</div>
                            </div>
                        </div>
                    </div>
                    <div id="two" class="e-panel" data-row="0" data-col="2" data-sizeX="5" data-sizeY="3">
                        <div class="e-panel-container">
                            <div class="text-align">
                                <div>2</div>
                            </div>
                        </div>
                    </div>
                    <div id="three" class="e-panel" data-row="0" data-col="7" data-sizeX="5" data-sizeY="3">
                        <div class="e-panel-container">
                            <div class="text-align">
                                <div>3</div>
                            </div>
                        </div>
                    </div>
                    <div id="four" class="e-panel" data-row="2" data-col="0" data-sizeX="2" data-sizeY="2">
                        <div class="e-panel-container">
                            <div class="text-align">
                                <div>4</div>
                            </div>
                        </div>
                    </div>
                    <div id="five" class="e-panel" data-row="4" data-col="2" data-sizeX="4" data-sizeY="3">
                        <div class="e-panel-container">
                            <div class="text-align">
                                <div>5</div>
                            </div>
                        </div>
                    </div>
                    <div id="six" class="e-panel" data-row="4" data-col="6" data-sizeX="3" data-sizeY="3">
                        <div class="e-panel-container">
                            <div class="text-align">
                                <div>6</div>
                            </div>
                        </div>
                    </div>
                    <div id="seven" class="e-panel" data-row="4" data-col="6" data-sizeX="3" data-sizeY="3">
                        <div class="e-panel-container">
                            <div class="text-align">
                                <div>7</div>
                            </div>
                        </div>
                    </div>
                    <div id="eight" class="e-panel" data-row="5" data-col="0" data-sizeX="2" data-sizeY="2">
                        <div class="e-panel-container">
                            <div class="text-align">
                                <div>8</div>
                            </div>
                        </div>
                    </div>
                </ejs-dashboardlayout>
              
              
            </div>
          </div>
        <div class="listbox1">
            <ejs-listbox id="listbox2" :dataSource='groupB' :allowDragAndDrop="true" :dragStart="dragStart" :fields="fields" :itemTemplate= "itemtemplate"  scope="combined-dashboard-layout"></ejs-listbox>
        </div>
    </div>
</template>

<script>
import Vue from "vue";
// Import syncfusion dashboardlayout component from layouts package
import { DashboardLayoutPlugin } from "@syncfusion/ej2-vue-layouts";
import { ListBoxPlugin } from "@syncfusion/ej2-vue-dropdowns";

Vue.use(ListBoxPlugin);
Vue.use(DashboardLayoutPlugin);

export default {
    data: function() {
        return {
          count: 8,
          spacing: [16,16],
          allowDragging: true,
          groupB: [
            { "Name": "India", "Code": "1" },
            { "Name": "Italy", "Code": "2" },
            { "Name": "Japan", "Code": "3" },
            { "Name": "Mexico", "Code": "4" },
            { "Name": "Norway", "Code": "5" },
            { "Name": "Poland", "Code": "6" },
            { "Name": "Switzerland", "Code": "7" },
            { "Name": "United Kingdom", "Code": "8" },
            { "Name": "United States", "Code": "9" }
        ],
        fields: { text: "Name" },
        itemtemplate:  "<div class='list-wrapper'><div class='name'>${Name}</div><div class='description'>${Code}</div></div>",
        };
    },
    methods: {
      ChangeCol(){
        debugger
        this.$refs.dashboard.$el.ej2_instances[0].movePanel("eight",0,0);
      },
      dragStart(e){
        let id = e.items[0].Code;
        this.dragStartDashboard();
      },
      dragStartDashboard(e){

      }
    },
}
</script>
<style scoped>
@import "../node_modules/@syncfusion/ej2-vue-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-layouts/styles/material.css";
.e-listbox-wrapper {
  margin: auto;
  max-width: 400px;
  box-sizing: border-box;
}

#container {
  box-sizing: border-box;
}

#container .e-listbox-wrapper:not(.e-list-template) .e-list-item {
  padding: 0;
  position: unset;
  cursor: pointer;
  height: 76px;
  line-height: normal;
}

.list-wrapper {
    height: inherit;
    position: relative;
    padding: 14px 12px 14px 78px;
}

.list-wrapper .text,
.list-wrapper .description {
  display: block;
  margin: 0;
  padding-bottom: 3px;
  white-space: normal;
}

.list-wrapper .description {
  font-size: 12px;
  font-weight: 500;
}

#container .e-listbox-wrapper .list-wrapper .text {
  font-weight: bold;
  font-size: 13px;
}

.e-dashboardlayout.e-control.e-responsive {
    background: #ffffff;
}
.listbox1{
  position: absolute;
  right: 0;
  top: 0;
  z-index: 1001;
  height: 71%;
  width: 200px;
  overflow: auto;
}
.name{
  font-size: 20px;

}

</style>