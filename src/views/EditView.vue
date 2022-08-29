<template>
<div>
  <MemoList/>
  <div v-if="memo">
    <div>
      <textarea cols="40" rows="15" v-model="memo.content"></textarea>
    </div>
    <div>
      <button @click="editMemo">編集</button>
      <button @click="deleteMemo">削除</button>
    </div>
  </div>
</div>
</template>

<script>
import MemoList from '../components/MemoList.vue'
export default {
  name: 'EditView',
  components: {
    MemoList
  },
  data () {
    return {
      memos: JSON.parse(localStorage.getItem('memos'))
    }
  },
  computed: {
    memo () {
      return this.memos.find(memo => memo.id === this.$route.params.id)
    }
  },
  methods: {
    editMemo () {
      localStorage.setItem('memos', JSON.stringify(this.memos))
      this.$router.push('/')
    },
    deleteMemo () {
      if (confirm('削除してよろしいですか？')) {
        this.memos = this.memos.filter(memo => memo.id !== this.$route.params.id)
        localStorage.setItem('memos', JSON.stringify(this.memos))
        this.$router.push('/')
      }
    }
  }
}
</script>

<style scoped>
  textarea {
    margin-bottom: 20px;
  }
  button {
    margin: 0 5px;
  }
</style>
