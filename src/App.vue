<template>
  <div id="app">
      <Tabs3D :tabItem="listTab" @changeStatus ="updateList"></Tabs3D>
    
  </div>
</template>

<script>
import Tabs3D from './components/Tabs3D.vue'

export default {
  name: 'App',
  components: {
    Tabs3D
  },
  data() {
    return {
      listTab: [
        {
          isEnable: true,
          name: 'First Tab',
          urlImg: "https://images.unsplash.com/photo-1564923630403-2284b87c0041?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1651&q=80",
          title: "First header",
          content: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt nu aliqua. Sollicit udin purus faucibus ornare aliquam ultrices sagittis orci a scelerisque a consectetur atna purus."
        },
        {
          isEnable: false,
          name: 'Second Tab',
          urlImg: "https://images.unsplash.com/photo-1542206395-9feb3edaa68d?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1600&q=80",
          title: "Second header",
          content: "Ac tortor vitae purus faucibus ornare suspendisse uis tristique sed nisi. Consectetur libero id ax faucibus in ornare faucibus nislt udin purus fi faucibus ac ornare aliquam ultrices in purus faucibu."
        },
        {
          isEnable: false,
          name: 'Third Tab',
          urlImg: "https://images.unsplash.com/photo-1548543604-a87c9909abec?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1268&q=80",
          title: "Third header",
          content: "Scelerisque fermentum dui faucibus in ornare id. Amet consectetur adipiscing elit duis tristique sollicitudin purus faucibus ornare aliquam ultrices sagittis nibh elit duis nubro tristique itae purus faucibus."
        }
      ]
    }
  },
  methods: {
    updateList(index) {
      this.listTab.forEach(element => {
        element.isEnable = false
      });
      this.listTab[index].isEnable = true
    }
  }
}
</script>

<style>
* {
    margin: 0;
    padding: 0;
}
body {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background: #43B0CB;
  color:#fff;
  font: 300 16px "Montserrat", sans-serif;
  line-height: 20px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}
</style>
