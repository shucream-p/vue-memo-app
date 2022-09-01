<template>
  <div>
    <MemoList :memos="memos"/>
    <div v-if="memo">
      <div>
        <textarea cols="40" rows="15" id="textarea" :value="memo.content" ref="textarea"></textarea>
      </div>
      <div>
        <button @click="editButtonClick">編集</button>
        <button @click="deleteButtonClick">削除</button>
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
  props: {
    memos: Array,
    memo: Object
  },
  emits: ['editButtonClick', 'deleteButtonClick'],
  mounted () {
    this.$refs.textarea.focus()
  },
  methods: {
    editButtonClick () {
      const updateMemo = document.getElementById('textarea').value
      this.$emit('editButtonClick', updateMemo)
    },
    deleteButtonClick () {
      this.$emit('deleteButtonClick')
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
