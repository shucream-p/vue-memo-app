<template>
  <div>
    <MemoList/>
    <div>
      <textarea cols="40" rows="15" v-model="newMemo"></textarea>
    </div>
    <div>
      <button @click="addMemo">保存</button>
    </div>
  </div>
</template>

<script>
import MemoList from '../components/MemoList.vue'

export default {
  name: 'NewView',
  components: {
    MemoList
  },
  data () {
    return {
      newMemo: '',
      memos: JSON.parse(localStorage.getItem('memos')) || []
    }
  },
  methods: {
    addMemo () {
      const title = this.newMemo.split('\n')[0]
      const memo = {
        id: new Date().getTime().toString(),
        title: title,
        content: this.newMemo
      }
      this.memos.push(memo)
      localStorage.setItem('memos', JSON.stringify(this.memos))
      this.$router.push('/')
    }
  }
}
</script>

<style scoped>
  textarea {
    margin-bottom: 20px;
  }
</style>
