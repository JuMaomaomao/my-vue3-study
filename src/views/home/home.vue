<template>
    <div>
        <setup :title="this.title"></setup>
        <t-divider align="center" dashed></t-divider>
        <hook></hook>
        <t-divider align="center" dashed></t-divider>
    </div>
</template>

<script>
import { ref } from 'vue'
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
        const callChildMethod = () => {
            childRef.value.foo()
        }
        callChildMethod()
    }
}
</script>

<style>
.t-layout__content {
    /* height: 100px; */
    padding: 20px;
}
</style>