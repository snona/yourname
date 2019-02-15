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
          <div v-if="count < max">
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
                <el-button type="success" size="mini" plain @click="failed(name)">{{name2}}</el-button>
              </el-col>
            </el-row>
            <el-row :gutter="20">
              <el-col :span="12" :xs="12">
                <el-button type="warning" size="mini" plain @click="failed(name)">{{name3}}</el-button>
              </el-col>
              <el-col :span="12" :xs="12">
                <el-button type="danger" size="mini" plain @click="failed(name)">{{name4}}</el-button>
              </el-col>
            </el-row>
            <el-progress :percentage="count*10"></el-progress>
            <div class="cc">{{cc}}</div>
          </div>
          <div v-else>
            <el-progress type="circle" :percentage="score*10"></el-progress>
            <el-button type="primary" size="mini" plain @click="reset()">Reset</el-button>
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
    var tnum2 = this.getRandomInt(cats.list.length);
    var tnum3 = this.getRandomInt(cats.list.length);
    var tnum4 = this.getRandomInt(cats.list.length);
    var tname2 = cats.list[tnum2].name;
    var tname3 = cats.list[tnum3].name;
    var tname4 = cats.list[tnum4].name;
    return {
      "max": 10,
      "count": 0,
      "score": 0,
      "p": require('~/assets/'+photo.src),
      "name": target.name,
      "name2": tname2,
      "name3": tname3,
      "name4": tname4,
      "cc": photo.cc,
      "able": false
    }
  },
  methods: {
    reset: function () {
      this.count = 0;
      this.score = 0;
      this.setQuestion(cats.list);
    },
    success: function (name) {
      this.$message({
        message: '正解' + name,
        type: 'success'
      });
      this.count += 1;
      this.score += 1;
      this.setQuestion(cats.list);
    },
    failed: function (name) {
      this.$message({
        message: '間違い' + name,
        type: 'error'
      });
      this.count += 1;
      this.setQuestion(cats.list);
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

      var tnum2 = this.getRandomInt(cats.list.length);
      var tnum3 = this.getRandomInt(cats.list.length);
      var tnum4 = this.getRandomInt(cats.list.length);
      var tname2 = cats.list[tnum2].name;
      var tname3 = cats.list[tnum3].name;
      var tname4 = cats.list[tnum4].name;

      this.name2 = tname2;
      this.name3 = tname3;
      this.name4 = tname4;
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
