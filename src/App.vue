<script setup>
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <div class="box" @contextmenu.prevent="showCustomMenu">
    <a target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>
    <h1>任意位置右键展示效果</h1>
  </div>
  <custom-context-menu ref="customMenu" :menu-items="[{label: '我去'},{lable: '卧槽'}]"></custom-context-menu>
  
</template>

<script>
import CustomContextMenu from './components/CustomContextMenu.vue'
export default {
  name: 'HelloWorld',
  components: {
    CustomContextMenu, // 注册子组件
  },
  data() {
    return {

    };
  },
  methods: {
    changeGreeting() {
      alert('你好哇')
    },
    showCustomMenu(event) {
      event.preventDefault(); // 阻止默认的右键菜单

      // 计算自定义菜单的位置（基于鼠标位置）
      const top = event.clientY;
      const left = event.clientX;

      console.log(this.$refs.customMenu)
      // 假设你有一个自定义菜单的Vue组件ref为"customMenu"
      this.$refs.customMenu.style.display = 'block'; // 显示自定义菜单
      this.$refs.customMenu.style.top = top + 'px';
      this.$refs.customMenu.style.left = left + 'px';

      // 可能还需要添加一些逻辑来处理菜单项的点击事件等
    },
  }
};
</script>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}

.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}

.box {
  position: fixed;
  height: 100%;
  width: 100%;
  top: 0;
  left: 0;
}
</style>
