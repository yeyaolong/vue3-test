<template>
    <div>
        <p>refCount的值为: {{refCount}}</p>
        <button @click="add">RefCount自增</button>
    </div>    
</template>

<script>
import { watchEffect, ref, reactive, toRefs } from '@vue/composition-api'
export default {
    setup() {

        const refCount = ref(0);

        const add = () => {
            refCount.value ++;
        };
         /**
         * watchEffact参数:
         *  监视的数据源（必须是一个函数）， 这里监视state.count与state.refCount的变化
         */
        // 默认初始化会先执行一次watch 这里监听的数据源取决于,回调函数里写的是什么，比如，回调函数里写的时refCount,那这个watchEffect监听的就是refCount
        watchEffect((a, b, c, d) => {
            console.log(refCount.value, a, b, c ,d)
        }, {
            flush: 'pre',   // pre 组件更新前触发 post(默认) 组件更新后触发 sync 与组件更新同步触发
            onTrack(event) {
                console.log('触发OnTrack',event);
            },
            onTrigger(event) {
                console.log('触发onTrigger', event);
            }
            // lazy: false  // 奇怪，我看这个composition-api的源代码用的是lazy，好像也没法阻止第一次立刻就执行
        })

        return {
            refCount,
            add
        }               
    },

}
</script>