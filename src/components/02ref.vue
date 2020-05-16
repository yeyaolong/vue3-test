<template>
    <div>
        refCount的值为: {{refCount}}
        <button @click="refCount++">自增</button>
    </div>
</template>

<script>
import { ref } from '@vue/composition-api'
export default {
    setup() {
        const refCount = ref(0);

        console.log(refCount);  // ref创建的是一个对象

        return {
            refCount
        };
    }
}
</script>