<template>
  <div class="main" ref="tile">
    <div class="menu">
      <ul>
        <li
          v-for="(item, index) in tabItem"
          :key="index"
          :class="{ enable: index + 1 === activeTab }"
          @click="changeHandle(index)"
        >
          {{ item.name }}
        </li>
      </ul>
    </div>
    <div class="body">
      <div class="content" v-for="item,index in tabItem" :key="index" v-show="item.isEnable" :style="setBackgroundImg(item.urlImg)">
        <div class="tab-image" ></div>
        <div class="tab-content">
          <h2>{{ item.title }}</h2>
          <p>{{ item.content }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import VanillaTilt from "vanilla-tilt";
export default {
  name: "App",
  props: {
    tabItem: Array,
  },
  data() {
    return {
      activeTab: 1,
    };
  },
  methods: {
    setBackgroundImg(urlImg) {
      return `background-image: url("${urlImg}"); background-size: cover; background-position: 0;`;
    },
    changeHandle(index) {
      this.activeTab = index + 1;
      this.$emit("changeStatus", index);
    },
  },
  mounted() {
    VanillaTilt.init(this.$refs.tile);
  },
};
</script>

<style scoped>
.main {
  width: 500px;
  height: 400px;
  background-color: blueviolet;
  border-radius: 5px;
  box-shadow: 0 5px 40px rgb(99, 97, 97);
  /* transform-style: preserve-3d; */
}
ul {
  height: 50px;
  line-height: 50px;
  background-color: #071011;
  color: rgb(189, 197, 204);
  list-style: none;
  border-top-right-radius: 5px;
  border-top-left-radius: 5px;
}
li {
  display: inline-block;
  width: 100px;
  cursor: pointer;
  padding: 0 10px;
  transition: all .5s linear;
}
.enable {
  background-color: #fff;
  color: rgb(102, 102, 107);
}
.tab-disable {
  display: none;
}
.tab-enable {
  display: none;
}
.content {
  height: 100%;
  box-sizing: border-box;
  text-align: left;
  position: relative;
}
.tab-image {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: block;
  background: rgba(0, 0, 0, 0.5);
  animation-name: example;
  animation-duration: .9s;
}
.tab-content {
  position: absolute;
  color: white;
  font: 300 16px "Montserrat", sans-serif;
  line-height: 24px;
  letter-spacing: 0.4px;
  padding: 20% 60px 20px 60px;
}

h2 {
  font-size: 40px;
  margin-bottom: 25px;
}
.body {
  height: 100%;
  position: relative;
}

@keyframes example {
  from {background: rgba(0, 0, 0, 0.3);}
  to {background: rgba(0, 0, 0, 0.5);}
}
</style>
