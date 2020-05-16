<template>
    <div class="">
        在reactive对象中访问ref创建的响应式数据：{{count}}
        <button @click="count++">自增</button>
    </div>
</template>

<script>
import {reactive, ref } from '@vue/composition-api';
export default {
    setup() {
        const count = ref(0);
        const state = reactive({
            count
        })

        // console.log(state.count);
        state.count++;  // 此处不需要通过 .value 就能直接访问原始值
        // console.log(count);


        // 新的ref会覆盖旧的ref
        const c1 = ref(0);
        const state2 = reactive({
            c1
        });

        const c2 = ref(9);
        state2.c1 = c2;
        state2.c1++;

        console.log(state2.c1);  // 10
        console.log(c2.value);  // 10
        console.log(c1.value); // 0

        return {
            count
        }
    }
}
</script>