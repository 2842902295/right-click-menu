<!-- 自定义右键菜单组件 CustomContextMenu.vue -->
<template>
    <ul class="custom-context-menu" v-show="isVisible">
        <li v-for="(item, index) in menuItems" :key="index" @click="handleMenuItemClick(item)">
            {{ item.label }}
        </li>
    </ul>
</template>

<script>
export default {
    props: ['menuItems'],
    data() {
        return {
            isVisible: true,
        };
    },
    methods: {
        handleMenuItemClick(item) {
            this.isVisible = false; // 点击后隐藏菜单
            // 执行对应的操作
            item.action();
        },
    },
    // ...
};
</script>

<style scoped>
.custom-context-menu {
    position: fixed;
    /* 添加样式以定位和样式化菜单 */
}
</style>