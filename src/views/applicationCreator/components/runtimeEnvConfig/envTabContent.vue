<template>
  <div>
    <el-radio-group v-model="environment.server">
      <el-radio-button :label="server" v-for="server in serverData" :key="server.server">{{server.server}}</el-radio-button>
    </el-radio-group>
    <!-- <div style="margin-left:-140px;">
      <el-form-item label="选择版本" required>
        <el-radio-group v-model="environment.version">
          <el-radio-button :label="version.id" v-for="version in versions" :key="version.id">{{version.label}}</el-radio-button>
        </el-radio-group>
      </el-form-item>
      <el-form-item label="资源配置" required>
        <el-radio-group v-model="environment.resource" class="left">
          <el-radio-button :label="resource.id" class="margin-r20 noradius border" v-for="resource in resources" :key="resource.id">{{resource.label}}</el-radio-button>
        </el-radio-group>
        <el-tooltip class="item" effect="dark" content="提示文字" placement="right">
          <i class="el-icon-question icon-q"></i>
        </el-tooltip>
      </el-form-item>
      <el-form-item label="子域名" required>
        <el-row class="left inlineBlock" style="width:85%;">
          <el-col :span="18">
            <div class="center">
              <el-input placeholder="请输入内容" v-model="environment.domain">
                <template slot="prepend">Http://</template>
                <template slot="append">{{domains.first}}</template>
              </el-input>
            </div>
          </el-col>
          <el-col class="center" :span="4">
            <div class="bg-purple-light">
              <div class="lastInput center">{{domains.last}}</div>
            </div>
          </el-col>
          <el-col style="width: 70px;">
            <el-tooltip effect="dark" content="提示文字" placement="right">
              <i class="el-icon-question icon-q"></i>
            </el-tooltip>
          </el-col>
        </el-row>
      </el-form-item>
    </div> -->
  </div>
</template>

<script>
export default {
  name: 'EnvTabContent',
  prop: {
    serverData: {
      type: Array,
      default: []
    }
  },
  data () {
    return {
      environment: {
        // name: '1',
        server: 'tomcat',
        version: '版本号1',
        resource: '1核2G',
        domain: ''
      },
      versions: [],
      resources: [],
      domains: {},
    }
  },
  mounted () {
    this.setEnvDefaultVal()
  },

  methods: {
    setEnvDefaultVal () {
      this.environment.server = this.serverData[0]
    }
  },
  watch: {
    'environment.server': function (val) {
      const {versions, resources, domains} = val
      this.versions = versions
      this.resources = resources
      this.domains = domains
      // 设置版本和资源默认值
      this.environment.resource = resources[0].id
      this.environment.version = versions[0].id
    }
  }
}
</script>

