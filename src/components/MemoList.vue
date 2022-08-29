<template>
  <div>
    <ul>
      <li v-for="memo in memos" :key="memo.id">
        <router-link :to="{ name: 'edit', params: { id: memo.id } }">
          {{ memo.title }}
        </router-link>
      </li>
      <li v-show="!memos.length">メモはありません</li>
      <li><router-link to="/new">+</router-link></li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'MemoList',
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
