<template>
  <div>
    <ul>
      <li v-for="memo in memos" :key="memo.id">{{memo.title}}</li>
      <li v-show="!memos.length">メモはありません</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeView',
  data() {
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