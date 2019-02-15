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
          <div>
            <el-row type="flex" justify="center">
              <el-col :span="20">
                <el-card :body-style="{ padding: '0px' }">
                  <img :src="p" class="image" />
                  <div style="padding: 14px;">
                    <span>???</span>
                  </div>
                </el-card>
              </el-col>
            </el-row>
            <el-row :gutter="20">
              <el-col :span="12" :xs="12">
                <el-button type="primary" size="mini" plain @click="success(name)">{{name}}</el-button>
              </el-col>
              <el-col :span="12" :xs="12">
                <el-button type="success" size="mini" plain>{{name}}</el-button>
              </el-col>
            </el-row>
            <el-row :gutter="20">
              <el-col :span="12" :xs="12">
                <el-button type="warning" size="mini" plain>{{name}}</el-button>
              </el-col>
              <el-col :span="12" :xs="12">
                <el-button type="danger" size="mini" plain>{{name}}</el-button>
              </el-col>
            </el-row>
            <el-progress :percentage="70"></el-progress>
            <div class="cc">{{cc}}</div>
          </div>
          <div>
            <el-progress type="circle" :percentage="25"></el-progress>
          </div>
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
    var tnum = this.getRandomInt(cats.list.length);
    var target = cats.list[tnum];
    var pnum = this.getRandomInt(target.photos.length);
    var photo = target.photos[pnum];
    return {
      "score": 20,
      "p": require('~/assets/'+photo.src),
      "name": target.name,
      "cc": photo.cc
    }
  },
  methods: {
    success: function (name) {
      this.$message({
        message: 'Congrats, this is a success message.' + name,
        type: 'success'
      });
      this.score += 1;
      this.setQuestion(cats.list)
    },
    getRandomInt(max) {
      return Math.floor(Math.random() * Math.floor(max));
    },
    setQuestion(list) {
      var tnum = this.getRandomInt(list.length);
      var target = list[tnum];
      var pnum = this.getRandomInt(target.photos.length);
      var photo = target.photos[pnum];

      this.p = require('~/assets/'+photo.src);
      this.name = target.name;
      this.cc = photo.cc;
    }
  },
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
  max-width: 100%;
  height: auto;
}

.cc {
  font-size: x-small;
  width: 400px;
}

.el-row {
  padding-bottom: 10px;
}

.el-card {
  width: 300px;
  height: 500px;
}

.el-main {
  width: 400px;
}
</style>
