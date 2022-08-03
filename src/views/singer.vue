<template>
  <div class="singer" v-loading="!singers.length">
    <index-list
    :data="singers"
    ></index-list>
  </div>
</template>

<script>
import { getSingerList } from '@/service/singer'
import indexList from '@/components/index-list/index-list'

  export default {
    name: 'singer',
    components: {
      indexList
    },
    data() {
      return {
        singers: []
      }
    },
    async created() {
      const result = await getSingerList()
      console.log("歌手数据:", result)
      this.singers = result.singers
    }
    
  }
</script>

<style lang="scss" scoped>
.singer{
  position: fixed;
  width: 100%;
  top: 88px;
  bottom: 0;
}
</style>