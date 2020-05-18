<template>
    <div>
        <h2>watch-02</h2>
        <p>count的值为: {{count}}</p>        
        <p>refCount的值为: {{refCount}}</p>
        <button @click="addCount">Count自增</button>
        <button @click="addRefCount">RefCount自增</button>
    </div>    
</template>

<script>
import { watchEffect, ref, reactive, toRefs, watch } from '@vue/composition-api'
export default {
    setup() {        
        /**
         * watchEffact参数:
         *  监视的数据源（必须是一个函数）， 这里监视state.count与state.refCount的变化
         */
        let state = reactive({
            count: 0,
            refCount: 1
        })
        watchEffect(() => {
            console.log(state.count);
            console.log(state.refCount);
        })

        watch(() => {
            console.log('watch state.count first function', state.count)
        }, (newVal, oldVal) => {
            console.log('watch state.count second function', newVal)
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