<template>
  <div>
    <el-tabs v-model="activeKey" @tab-click="handleTabClick">
      <el-tab-pane label="Tab 1" name="1">
        <div>
          <h1>Handsontable Demo - Tab 1</h1>
          <div style="height: 400px; overflow-x: auto;">
            <div id="hot"></div>
          </div>
        </div>
      </el-tab-pane>
      <el-tab-pane label="Tab 2" name="2">
        <div>
          <h1>Handsontable Demo - Tab 2</h1>
          <div>{{ tab2Data }}</div>
        </div>
      </el-tab-pane>
      <el-tab-pane label="Tab 3" name="3">
        <div>
          <h1>Handsontable Demo - Tab 3</h1>

        </div>
      </el-tab-pane>
    </el-tabs>
  </div>
</template>



<script>
import Handsontable from 'handsontable';
import 'handsontable/dist/handsontable.full.css';
import "handsontable/languages/zh-CN";

export default {
  data() {
    return {
      activeKey: '1',
      tab2Data: 'Content of Tab Pane 2',
      data: [
        ['qwe', 'B1', 'C1'],
        ['A2', 'B2', 'C2'],
        ['A3', 'B3', 'C3'],
      ],
    };
  },
  methods: {
    handleTabClick(tab) {
      this.activeKey = tab.name;
    }
  },
  mounted() {

    const container = document.getElementById('hot');
    const data = [
      ['qwe', 'B1', 'C1'],
      ['A2', 'B2', 'C2'],
      ['A3', 'B3', 'C3'],
    ];
    const hot = new Handsontable(container, {
      colHeaders: [
        "Company name",
        "Country",
        "Name",
        "Sell date",
        "Order ID",
        "In stock",
        "Qty",
        "Progress",
        "Rating"
      ],
      //表格数据
      data:this.data,
      //表格整体宽度
      width: '100%',
      //行表头
      rowHeaders: true,
      //列表头

      //合并单元格
      mergeCells: true,
      //单元格属性
      cell:[],
      //右键菜单
      contextMenu: true,
      //自动拉伸
      stretchH: 'all',
      autoWrapRow: true,
      //下拉菜单
      dropdownMenu: true,
      columnSorting: {
        indicator: true
      },
      autoColumnSize: {
        samplingRatio: 23
      },
      //默认语言
      language: "zh-CN",
      //默认对齐方式
      className: "htCenter htMiddle",
      //许可证
      licenseKey: 'ab3e4-1bee8-ed01c-4d94b-08cfe',
      //导出文件插件
      exportFile: true,
      //公式插件
      formulas:true,
      //评论插件
      filters: true, // 启用基本的筛选功能
      comments:true,
      minSpareRows:40,
      minSpareCols:10,
      manualRowResize: true,
      manualColumnResize: true,
      manualColumnMove: true,
      manualRowMove: true,
    });
    },
}
</script>

<style>
#hot {
  width: 100%;
  height: 400px;
  margin: 20px auto;
}

</style>
