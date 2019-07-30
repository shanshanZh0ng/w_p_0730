<template>
    <div class="environment">
      <div class="margBot15 pad_t10">
        <i class="el-icon-s-management baseBlue"></i>
        <span>{{title}}</span>
      </div>
        <Card :cardName="cardName" :handleBtn="handleBtn" :nameIndex="$attrs.nameIndex">
          <el-form label-width="140px" class="demo-ruleForm">
            <el-form-item label="选择模板/镜像" required>
              <el-tabs v-model="name" class="inlineBlock left">
                <el-tab-pane label="运行时" name="1">
                  <EnvTabContent :serverData="serverData"></EnvTabContent>
                </el-tab-pane>
                <el-tab-pane label="我的镜像" name="2">
                  <!-- <div>
                    <el-radio-group v-model="mirror.server">
                      <el-radio-button :label="server" v-for="server in mirrorData" :key="server.server">{{server.server}}</el-radio-button>
                    </el-radio-group>
                  </div> -->
                </el-tab-pane>
              </el-tabs>
            </el-form-item>
            <!-- <el-form-item label="选择版本" required>
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
            </el-form-item> -->
          </el-form>
        </Card>
    </div>
</template>

<script>
import Card from '@/components/card'
import EnvTabContent from './envTabContent'

export default {
  name: 'Environment',
  data () {
    return {
      title: '环境设置',
      cardName: 'environment',
      handleBtn: false,
      name: '1',
      // environment: {
      //   name: '1',
      //   server: 'tomcat',
      //   version: '版本号1',
      //   resource: '1核2G',
      //   domain: ''
      // },
      // versions: [],
      // resources: [],
      // domains: {},
      serverData: [
        {
          server: 'tomcat',
          versions: [{label: '版本号1.0', id: 1}, {label: '版本号2', id: 2}],
          resources: [{label: '1核2G', id: 1}, {label: '2核4G', id: 2}, {label: '4核8G', id: 3}],
          domains: {first: 'inatance.paas.casicloud.com', last: '27017'},
          id: 1
        },
        {
          server: 'apache',
          versions: [{label: '版本号1.0.1', id: 1}, {label: '版本号2', id: 2}],
          resources: [{label: '1核2G2', id: 1}, {label: '2核4G', id: 2}, {label: '4核8G', id: 3}],
          domains: {first: 'inatance.paas.casicloud.com', last: '27017'},
          id: 2
        },
        {
          server: 'golang',
          versions: [{label: '版本号1.2', id: 1}, {label: '版本号2', id: 2}],
          resources: [{label: '1核2G3', id: 1}, {label: '2核4G', id: 2}, {label: '4核8G', id: 3}],
          domains: {first: 'inatance.paas.casicloud.com', last: '27017'},
          id: 3
        },
        {
          server: 'nginx',
          versions: [{label: '版本号1.4', id: 1}, {label: '版本号2', id: 2}],
          resources: [{label: '1核2G4', id: 1}, {label: '2核4G', id: 2}, {label: '4核8G', id: 3}],
          domains: {first: 'inatance.paas.casicloud.com', last: '27017'},
          id: 4
        },
        {
          server: 'node',
          versions: [{label: '版本号1.5', id: 1}, {label: '版本号2', id: 2}],
          resources: [{label: '1核2G5', id: 1}, {label: '2核4G', id: 2}, {label: '4核8G', id: 3}],
          domains: {first: 'inatance.paas.casicloud.com', last: '27017'},
          id: 5
        },
        {
          server: 'python',
          versions: [{label: '版本号1.6', id: 1}, {label: '版本号2', id: 2}],
          resources: [{label: '1核2G6', id: 1}, {label: '2核4G', id: 2}, {label: '4核8G', id: 3}],
          domains: {first: 'inatance.paas.casicloud.com', last: '27017'},
          id: 6
        },
        {
          server: 'rudy',
          versions: [{label: '版本号1.7', id: 1}, {label: '版本号2', id: 2}],
          resources: [{label: '1核2G7', id: 1}, {label: '2核4G', id: 2}, {label: '4核8G', id: 3}],
          domains: {first: 'inatance.paas.casicloud.com', last: '27017'},
          id: 7
        },
        {
          server: 'dotnet',
          versions: [{label: '版本号1.8', id: 1}, {label: '版本号2', id: 2}],
          resources: [{label: '1核2G8', id: 1}, {label: '2核4G', id: 2}, {label: '4核8G', id: 3}],
          domains: {first: 'inatance.paas.casicloud.com', last: '27017'},
          id: 8
        }
      ],
      mirrorData: [
        {
          server: 'tomcat',
          versions: [{label: 'm版本号1.0', id: 1}, {label: 'm版本号2', id: 2}],
          resources: [{label: 'm1核2G', id: 1}, {label: 'm2核4G', id: 2}, {label: 'm4核8G', id: 3}],
          domains: {first: 'inatance.paas.casicloud.com', last: '27017'},
          id: 1
        },
        {
          server: 'apache',
          versions: [{label: '版本号1.0.1', id: 1}, {label: '版本号2', id: 2}],
          resources: [{label: '1核2G2', id: 1}, {label: '2核4G', id: 2}, {label: '4核8G', id: 3}],
          domains: {first: 'inatance.paas.casicloud.com', last: '27017'},
          id: 2
        }
      ]
    }
  },

  // mounted () {
  //   this.setEnvDefaultVal()
  // },

  // methods: {
  //   setEnvDefaultVal () {
  //     this.environment.server = this.serverData[0]
  //   }
  // },

  components: {
    Card
  }

  // watch: {
  //   'environment.server': function (val) {
  //     const {versions, resources, domains} = val
  //     this.versions = versions
  //     this.resources = resources
  //     this.domains = domains
  //     // 设置版本和资源默认值
  //     this.environment.resource = resources[0].id
  //     this.environment.version = versions[0].id
  //   }
  // }
}
</script>

<style scoped>
  .lastInput {
    border: 1px solid #ccc;
    border-left:none;
    color:#909399;
    height:38px;
    line-height:38px;
    background:#F5F7FA;
  }
</style>
