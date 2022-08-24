<template>
  <div>
    <h2>新規メモ</h2>
    <div>
      <textarea cols="40" rows="15" v-model="newMemo"></textarea>
    </div>
    <div>
      <button @click.prevent="addMemo">保存</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'NewView',
  data() {
    return {
      newMemo: '',
      memos: []
    }
  },
  methods: {
    addMemo() {
      const title = this.newMemo.split('\n')[0]
      const memo = {
        id: new Date().getTime().toString(),
        title: title,
        content: this.newMemo
      }
      this.memos.push(memo)
      this.newMemo = ''
      localStorage.setItem('memos', JSON.stringify(this.memos))
    }
  }
}
</script>

<style scoped>
  textarea {
    margin-bottom: 20px;
  }
</style>
