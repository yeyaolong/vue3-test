<template>
  <div>{{ count }} {{ object.foo }}</div>
</template>

<script>
  import { ref, reactive } from '@vue/composition-api'

  export default {
    setup() {
      const count = ref(0)
      const object = reactive({ foo: 'bar' })

      // expose to template
      return {
        count,
        object
      }
    }
  }
</script>