<template>
  <section class="container">
    <div>
      <el-card :body-style="{ padding: '0px' }">
        <img :src="p" class="image" />
        <div style="padding: 14px;">
          <span>???</span>
        </div>
      </el-card>
      <div>
        <el-button type="primary" size="mini" plain>{{name}}</el-button>
        <el-button type="success" size="mini" plain>{{name}}</el-button>
        <el-button type="warning" size="mini" plain>{{name}}</el-button>
        <el-button type="danger" size="mini" plain>{{name}}</el-button>
      </div>
      <span class="cc">{{cc}}</span>
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
