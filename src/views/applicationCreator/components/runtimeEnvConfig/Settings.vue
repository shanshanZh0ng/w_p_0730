<template>
  <div class="settings">
    <el-row class="margBot15" style="padding-left:16px;">
      <i class="el-icon-setting"></i>
      <span style="margin-right:20px;font-size:14px;">选择配置项</span>
      <!-- <el-checkbox-group @change="handleChange" v-model="checkValue" class="inlineBlock">
        <el-checkbox
          v-for="item in settings"
          :key="item.name"
          :label="item"
          border
          size="medium"
        >{{item.name}}</el-checkbox>
      </el-checkbox-group> -->
        <el-checkbox
          v-for="item in settings"
          :key="item.name"
          :label="item"
          @change="handleChange"
          border
          v-model="item.value"
          size="medium"
        >{{item.name}}</el-checkbox>
      <i class="el-icon-info" style="color:#E6A23C;"></i>
      <span class="tip-text">根据实际情况，创建数据库或存储实例，系统会为您自动绑定应用。</span>
    </el-row>
  </div>
</template>

<script>
export default {
  props: {
    settings: {
      type: Array,
      default: () => [
        {name: '存储', value: false, id: 1, alias: 'storage'},
        {name: '数据库', value: false, id: 2, alias: 'dataBase'}
      ]
    }
  },
  name: 'Settings',
  data () {
    return {
      checkValue: []
    }
  },
  methods: {
    handleChange (val) {
      let data = this._makeEmitData(this.settings)
      this.$emit('setting-change', data)
    },
    _makeEmitData (values) {
      const data = Object.create(null)

      this.settings.forEach(val => {
        let key = val.alias
        let value = val.value
        data[key] = value
      })
      return data
    }
  }
}
</script>

<style scoped>
  .inlineBlock {
    display: inline-block;
  }
</style>
