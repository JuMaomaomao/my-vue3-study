<template>
    <div>
        <setup :title="this.title" ref="childRef"></setup>
        <t-divider align="center" dashed></t-divider>
        <hook></hook>
        <t-divider align="center" dashed></t-divider>
    </div>
</template>

<script>
import { ref, onMounted } from 'vue'
import Setup from '../../components/setup/setup.vue';
import Hook from '../../components/hook/hook.vue';
export default {
    components: { Setup, Hook },
    name: "Home",
    data: function () {
        return {
            title: "这是一个标题"
        }
    },
    setup() {
        const childRef = ref()
        onMounted(() => {
            console.log(childRef.value);
            childRef.value.foo() // 调用
        })
        return {
            childRef
        }
    }
}
</script>

<style>
.t-layout__content {
    /* height: 100px; */
    padding: 20px;
}
</style>