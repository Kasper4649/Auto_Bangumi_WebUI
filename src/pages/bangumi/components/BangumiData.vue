<script setup lang="ts">
const store = bangumiStore();

const activeName = ref('1');
const dialogData = ref(null);
const dialog = ref();

onActivated(() => {
  store.get();
});
</script>

<template>
  <ShowResults ref="dialog" title="执行结果" :results="dialogData" />

  <div class="bangumi-data">
    <el-collapse v-model="activeName" accordion>
      <el-collapse-item title="已订阅番剧" name="1">
        <span class="tips"
          >注: 目前只能管理 mikan 源, 如通过 api 添加其他来源的新番将
          <b>不会</b> 出现在此处</span
        >
        <el-table
          :data="store.data.bangumi_info"
          stripe
          border
          style="width: 100%"
          max-height="40vh"
        >
          <el-table-column prop="official_title" label="番名" min-width="250" />
          <el-table-column prop="season" label="季度" width="60" />
          <el-table-column prop="dpi" label="分辨率" />
          <el-table-column prop="subtitle" label="字幕" />
          <el-table-column prop="group" label="字幕组" />
        </el-table>
      </el-collapse-item>
    </el-collapse>
  </div>
</template>

<style lang="scss" scope>
.bangumi-data {
  .tips {
    line-height: 2;
    color: #f56c6c;
    display: inline-block;
    margin-bottom: 10px;
  }
}
</style>
