<template>
  <div>
    <MemoList/>
  </div>
</template>

<script>
import MemoList from '../components/MemoList.vue'

export default {
  name: 'HomeView',
  components: {
    MemoList
  },
  data () {
  return {
    memos: JSON.parse(localStorage.getItem('memos')) || []
  }
}
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
