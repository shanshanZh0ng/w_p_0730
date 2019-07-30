<template>
  <div class="application">
    <BaseConfig></BaseConfig>
    <RuntimeEnv></RuntimeEnv>
    <el-row class="mainBtnD">
      <el-button>取消</el-button>
      <el-button type="primary">创建</el-button>
    </el-row>
  </div>
</template>

<script type="text/ecmascript-6">
import BaseConfig from './components/baseConfig/BaseConfig'
import RuntimeEnv from './components/runtimeEnvConfig/index'

export default {
  name: 'ApplicationCreate',
  data () {
    return {
    }
  },
  components: {
    BaseConfig,
    RuntimeEnv
  },
  methods: {
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.application {
  padding-bottom: 60px;
  margin: 20px;
}
</style>
