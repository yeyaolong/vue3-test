<template>
    <div>
        <p>count的值为: {{count}}</p>        
        <p>refCount的值为: {{refCount}}</p>
        <button @click="addCount">Count自增</button>
        <button @click="addRefCount">RefCount自增</button>
    </div>    
</template>

<script>
import { watchEffect, ref, reactive, toRefs } from '@vue/composition-api'
export default {
    setup() {

        // const refCount = ref(0);

        // const add = () => {
        //     refCount.value ++;
        // };

        // // 默认初始化会先执行一次watch 这里监听的数据源取决于,回调函数里写的是什么，比如，回调函数里写的时refCount,那这个watchEffect监听的就是refCount
        // watchEffect(() => {
        //     console.log(refCount.value)
        // })

        // return {
        //     refCount,
        //     add
        // }

        const state = reactive({
            count: 0,
            refCount: 99
        })
        /**
         * watchEffact参数:
         *  监视的数据源（必须是一个函数）
         *  回调函数
         */
        watchEffect(() => state.count, (newVal, oldVal) => {
            console.log(state.count)
            console.log(newVal, oldVal)
        })

        const addCount = function() {
            state.count++;
            
        }

        const addRefCount = function () {
            state.refCount++;
        }

        return {
            ...toRefs(state),
            addCount,
            addRefCount
        }
    }
}
</script>