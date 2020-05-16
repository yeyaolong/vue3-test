<template>
    <div>
        count值为： {{count}} 
        <!-- 这里并不能使用state.count, 否则直接报错: {{state.count}}    -->

        <button @click="count +=1">递增</button>
    </div>    
</template>

<script>
import { reactive } from '@vue/composition-api'

export default {
    
    setup(props, context) {
        // console.log('setup');
        // console.log('props', props);
        // console.log('context', context);
        // console.log('在setup中this已经不能使用了, context替代了this', this);
        const state = reactive({count: 0});

        // console.log(state);
        state.count ++;
        // console.log(state);

        return state;
    },

    beforeCreate() {
        // console.log('beforeCreate')
    },

    created() {
        // console.log('created')
    },
    props: {
        p1: String,
    }
}
</script>