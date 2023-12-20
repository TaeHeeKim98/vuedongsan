<template>

  <div class="black-bg" v-if="modal">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>상세페이지 내용 &nbsp;&nbsp;
        <span id="close" @click="modal_close()" style="cursor: pointer;">close</span>
      </p>
    </div>
  </div>

  <div class="menu">
    <a href="" v-for="menu in menus" :key="menu">
      {{ menu }} 
    </a>
  </div>

  <div :key="index" v-for="(item, index) in products">
    <img :src="products[index].image" alt="" class="img">
    <h4 @click="modal_open()" style="cursor: pointer;">{{ products[index].title }}</h4>
    <p>{{ products[index].content }}</p>
    <p>가격 : {{ products[index].price }}원</p>
  </div>

</template>

<script>

import datas from './assets/data.js';

export default {
  name: 'App',
  data() {
    return {
      products : datas,
      menus : ['Home','Shop','About'],
      modal : false
    }
  },
  components: {
    
  },
  methods : {
    increase(idx) {
      this.num[idx] += 1;
    },
    modal_open() {
      this.modal = true
    },
    modal_close() {
      this.modal = false
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  text-decoration: none;
  color: white;
  padding: 10px;
}

.img {
  width: 100%;
}

body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

.black-bg {
  width: 100%; height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}

.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}

</style>
