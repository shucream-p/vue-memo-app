<template>
  <div>
    <MemoList :memos="memos"/>
  </div>
</template>

<script>
import MemoList from '../components/MemoList.vue'

export default {
  name: 'HomeView',
  components: {
    MemoList
  },
  props: {
    memos: Array
  },
}
</script>

<style scoped>
ul {
  padding: 0;
}
li {
  list-style: none;
}
</style>
