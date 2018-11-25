<template>
  <div>
    {{msg}}
    <Map/>
  </div>
</template>

<script>
import Map from '@/components/Map'

export default {
  name: 'TopPage',
  data () {
    return {
      msg: 'this is topPage'
    }
  },
  components: {
    Map
  }
}
</script>

<style>

</style>
