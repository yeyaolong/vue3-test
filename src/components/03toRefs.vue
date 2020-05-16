<template>
    <div>
        <p>count值为{{count}}</p>
        <button @click="add">自增</button>
    </div>
</template>

<script>
import { reactive, toRefs } from '@vue/composition-api'
export default {
    setup() {
        const state = reactive({
            count: 0,
            name: '张三'
        })

        // 定义自增+1的函数,相当于Vue 2.X的methods
        const add = () => {
            state.count++;
        }
        /**
         * 这里不能用 ES6 的展开运算符张开 state
         * 也即 
         * return {
         *  ...state,
         * add
         * }
         * 会导致
         * 在template中使用时，{{count}}不再是响应式的
         */
        // 解决方案1
        /**
         * return {
         *  state,
         *  add
         * }
         * 在template中使用时，{{state.count}}, 仍然是响应式的
         */
        // return {
        //      state,
        //      add
        //  };
        // 解决方案2
        return {
            // 将 state 上的每个属性，都转化为 ref 形式的响应式数据
            ...toRefs(state),
            add
        }
    }
}
</script>