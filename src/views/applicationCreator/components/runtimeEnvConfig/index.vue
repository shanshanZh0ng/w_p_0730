<template>
  <div>
    <div class="margBot15 pad_t10">
      <i class="el-icon-s-management baseBlue"></i>
      <span>运行环境设置</span>
      <el-tooltip class="item" effect="dark" content="提示文字" placement="right">
        <i class="el-icon-question icon-q"></i>
      </el-tooltip>
    </div>
    <el-card class="box-card">
      <div class="title">
        <el-button
          size="small"
          @click="addTab(tab.editableTabsValue)"
        >
          添加运行环境
        </el-button>
      </div>
      <el-tabs v-model="tab.editableTabsValue" type="card" closable @tab-remove="removeTab">
        <el-tab-pane
          :key="tab.name"
          v-for="(tab, index) in tab.editableTabs"
          :label="`${appName}${tab.name}`"
          :name="tab.name"
        >
          <Settings @setting-change="(val) => settingChange(val, tab)" ></Settings>
          <Storage :nameIndex="index+1" v-show="tab.configs.storage"></Storage>
          <DataBase :nameIndex="index+1"  v-show="tab.configs.dataBase"></DataBase>
          <Environment :nameIndex="index+1"></Environment>
        </el-tab-pane>
      </el-tabs>
    </el-card>
  </div>
</template>

<script>
// import Card from '@/components/Card'
import Settings from './Settings'
import DataBase from './Database'
import Storage from './Storage'
import Environment from './Environment'

export default {
  name: 'RuntimeEnv',
  data () {
    return {
      tab: {
        editableTabsValue: '1',
        editableTabs: [{
          title: '应用名1',
          name: '1',
          content: 'Tab 1 content',
          configs: {
            storage: false,
            database: false
          }
        }],
        tabIndex: 1
      }
    }
  },
  components: {
    // Card,
    Settings,
    DataBase,
    Storage,
    Environment
  },
  computed: {
    appName () {
      return this.$store.state.application.name
    }
  },
  methods: {
    settingChange (val, tab) {
      tab.configs = val
    },
    addTab (targetName) {
      let newTabName = ++this.tab.tabIndex + ''
      this.tab.editableTabs.push({
        // title: `${this.appName}${newTabName}`,
        name: newTabName,
        content: 'New Tab content',
        configs: {
          storage: false,
          database: false
        }
      })
      this.tab.editableTabsValue = newTabName
    },
    removeTab (targetName) {
      let tabs = this.tab.editableTabs
      let activeName = this.tab.editableTabsValue
      if (activeName === targetName) {
        tabs.forEach((tab, index) => {
          if (tab.name === targetName) {
            let nextTab = tabs[index + 1] || tabs[index - 1]
            if (nextTab) {
              activeName = nextTab.name
            }
          }
        })
      }
      this.tab.editableTabsValue = activeName
      this.tab.editableTabs = tabs.filter(tab => tab.name !== targetName)
    }
  }
}
</script>

<style scoped>
</style>
