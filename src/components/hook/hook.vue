<template>
    <div class="tdesign-demo-item--base">
        <div>
            <t-layout>
                <t-header>生命周期钩子</t-header>
                <t-content>Content</t-content>
            </t-layout>
        </div>
    </div>
</template>

<script>
import { onMounted } from 'vue'
export default {
    name: "Hook",
    setup() {
        // 组件内使用生命周期函数
        onMounted(() => {
            console.log("Component is mounted!");
        })
    }
}
</script>

<style>
</style>