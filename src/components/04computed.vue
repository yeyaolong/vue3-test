<template>
    <div>
        <p>count的值是: {{refCount}}</p>
        <p>plusOne的值是: {{plusOne}}</p>
        <button @click="add">自增</button>
        <button @click="set">设置computed的值</button>
    </div>
</template>

<script>
import { computed, ref } from '@vue/composition-api'
export default {
    setup(props, context) {
        let refCount = ref(1);

        let plusOne = computed({
            get: () => {
                return refCount.value + 1
            },
            set: (val) => {
                console.log(val)
                refCount.value = val -1;
            }
        });

        const add = () => {
            refCount.value++;
        }

        const set = () => {
            plusOne.value = 10;
        }

        return {
            refCount,
            plusOne,
            add,
            set
        }
    }
}
</script>