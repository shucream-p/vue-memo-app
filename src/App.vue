<template>
  <div>
    <h1>メモアプリ</h1>
    <router-view :memos="memos" :memo="memo" @create-button-click="createMemo" @update-button-click="updateMemo" @delete-button-click="deleteMemo"/>
  </div>
</template>

<script>
export default {
  name: 'App',
  data () {
    return {
      memos: JSON.parse(localStorage.getItem('memos')) || []
    }
  },
  computed: {
    memo () {
      return this.memos.find(memo => memo.id === this.$route.params.id)
    }
  },
  methods: {
    saveLocalStorage () {
      localStorage.setItem('memos', JSON.stringify(this.memos))
      this.$router.push('/')
    },
    createMemo (content) {
      const memo = {
        id: new Date().getTime().toString(),
        content
      }
      this.memos.push(memo)
      this.saveLocalStorage()
    },
    updateMemo (content) {
      this.memo.content = content
      this.saveLocalStorage()
    },
    deleteMemo () {
      if (confirm('削除してよろしいですか？')) {
        this.memos = this.memos.filter(memo => memo.id !== this.$route.params.id)
        this.saveLocalStorage()
      }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
