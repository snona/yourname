<template>
  <section class="container">
    <div>
      <el-container>
        <el-header style="text-align: right; font-size: 12px">
          <el-dropdown>
            <i class="el-icon-setting" style="margin-right: 15px"></i>
            <el-dropdown-menu slot="dropdown">
              <el-dropdown-item>View</el-dropdown-item>
            </el-dropdown-menu>
          </el-dropdown>
          <span>Tom</span>
        </el-header>
        <el-main>
          <div>{{score}}</div>
          <el-card :body-style="{ padding: '0px' }">
            <img :src="p" class="image" />
            <div style="padding: 14px;">
              <span>???</span>
            </div>
          </el-card>
          <el-row :gutter="20">
            <el-col :span="6"><el-button type="primary" size="mini" plain>{{name}}</el-button></el-col>
            <el-col :span="6"><el-button type="success" size="mini" plain>{{name}}</el-button></el-col>
            <el-col :span="6"><el-button type="warning" size="mini" plain>{{name}}</el-button></el-col>
            <el-col :span="6"><el-button type="danger" size="mini" plain>{{name}}</el-button></el-col>
          </el-row>
          <el-progress :percentage="70"></el-progress>
          <span class="cc">{{cc}}</span>
        </el-main>
      </el-container>
    </div>
  </section>
</template>

<script>
import cats from '~/assets/cats.json';

export default {
  components: {
  },
  data: function () {
    return {
      "score": 20,
      "p": require('~/assets/'+cats.list[0].photos[0].src),
      "name": cats.list[0].name,
      "cc": cats.list[0].photos[0].cc
    }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}

.image {
  width: 300px;
}

.cc {
  font-size: x-small;
}
</style>
