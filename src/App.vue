<template>
  <div>
    <h1>メモアプリ</h1>
    <router-view :memos="memos" :memo="memo" @create-button-click="createMemo" @edit-button-click="editMemo" @delete-button-click="deleteMemo"/>
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
    createMemo (e) {
      const title = e.split('\n')[0]
      const memo = {
        id: new Date().getTime().toString(),
        title: title,
        content: e
      }
      this.memos.push(memo)
      this.saveLocalStorage()
    },
    editMemo (e) {
      this.memo.title = e.split('\n')[0]
      this.memo.content = e
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
