<template>
    <!-- 监听多个数据源  -->
    <div class="watch-03">
        <div class="boy">
            男生数量{{boys.count}}
        </div>
        <div class="girl">
            女生数量{{girls.count}}
        </div>

        <button @click="addGirl">女生增加</button>
        <button @click="addBoy">男生增加</button>
    </div>
</template>

<script>
import { reactive, watchEffect, toRefs } from '@vue/composition-api'
export default {
    setup(props, context) {
        const state = reactive({
            boys: {
                count: 0,
                name: '男生数量'
            },
            girls: {
                count: 0,
                name: '女生数量'
            }
        });
        // 在一个watchEffect中监听多个数据源
        watchEffect(() => {
            console.log(`男生数量:${state.boys.count}`);
            console.log(`女生数量:${state.girls.count}`);
        }, {
            // composition-api中的第二个参数options 暂时配置无效，我没有查到原因
        })

        const addBoy = () => {
            state.boys.count++;
        }

        const addGirl = () => {
            state.girls.count++;
        }

        return {
            ...toRefs(state),
            addBoy,
            addGirl
        }
    }
}
</script>