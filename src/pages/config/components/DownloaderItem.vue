<script lang="ts" setup>
import { downloaderType, form, tfOptions } from '../form-data';

const downloader = computed(() => form.downloader);
</script>

<template>
  <ConfigFormRow title="下载器设置">
    <ConfigFormCol label="下载器">
      <el-select v-model="downloader.type" flex-1>
        <el-option
          v-for="opt in downloaderType"
          :key="opt"
          :value="opt"
        ></el-option>
      </el-select>
    </ConfigFormCol>

    <ConfigFormCol label="下载器地址" prop="downloader.host">
      <el-input v-model="downloader.host"></el-input>
    </ConfigFormCol>

    <ConfigFormCol label="下载路径(映射后)">
      <el-input v-model="downloader.path"></el-input>
    </ConfigFormCol>

    <ConfigFormCol label="用户名">
      <el-input v-model="downloader.username"></el-input>
    </ConfigFormCol>

    <ConfigFormCol label="密码">
      <el-input v-model="downloader.password"></el-input>
    </ConfigFormCol>

    <ConfigFormCol label="ssl">
      <el-select v-model="downloader.ssl" flex-1>
        <el-option
          v-for="(opt, index) in tfOptions"
          :key="index"
          :label="opt.label"
          :value="opt.value"
        ></el-option>
      </el-select>
    </ConfigFormCol>
  </ConfigFormRow>
</template>
