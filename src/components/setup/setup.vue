<template>
    <div class="tdesign-demo-item--base">
        <div>
            <t-layout>
                <t-header>setup</t-header>
                <t-content>
                    <t-row></t-row>
                    <t-row :gutter="18">
                        <t-col :span="2">
                            <t-addon prepend="watch: ">
                                <t-input placeholder="请输入内容" v-model="num" />
                            </t-addon>
                        </t-col>

                        <t-col :span="2">
                            <t-addon prepend="computed: ">
                                <t-input placeholder="请输入内容" v-model="doubleNum" />
                            </t-addon>
                        </t-col>

                        <t-col :span="2">
                            <t-button theme="primary" @click="numAdd">自增</t-button>
                        </t-col>

                        <t-col :span="2"></t-col>
                        <t-col :span="2"></t-col>
                        <t-col :span="2"></t-col>
                    </t-row>
                </t-content>
            </t-layout>
        </div>
    </div>
</template>
<script>
import { ref, watch, computed, toRefs, toRef, h } from 'vue'
export default {
    name: 'Setup',
    props: {
        title: String
    },
    setup(props, context) {
        // 不能使用解构来拿到props里的参数，解构会使props失去响应性
        // 使用toRefs来拿到参数
        const { title } = toRefs(props)
        console.log('title: ', title.value);

        const foo = function () {
            console.log("子组件中的方法");
        }


        // const xxx = ref()
        // console.log(xxx.value);

        // ref函数
        let num = ref(0)
        console.log('num: ', num) // {_shallow: false, dep: undefined, __v_isRef: true, _rawValue: 0, _value: 0}
        console.log('num.value: ', num.value); // 0



        // 点击自增
        const numAdd = () => {
            num.value++
        }

        // 监听num
        watch(num, (newValue, oldValue) => {
            console.log('oldValue: ', oldValue, 'newValue: ', newValue);
        })

        // 计算属性 
        const doubleNum = computed(() => num.value * 5)

        // return {
        //     numAdd,
        //     num,
        //     doubleNum,
        // }

        // 返回一个渲染函数会阻止我们返回其他参数，我们可以使用expose使参数暴露出去

        defineExpose({
            // numAdd,
            // num,
            // doubleNum,
            foo
        })

        // return () => h('div', [title.value])
    },
    created() {
        console.log("setup外使用created");
    }
}
</script>