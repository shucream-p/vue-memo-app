<template>
  <div>
    <MemoList :memos="memos"/>
    <div v-if="memo">
      <div>
        <textarea cols="40" rows="15" v-model="memo.content"></textarea>
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
    memos: Array
  },
  computed: {
    memo () {
      return this.memos.find(memo => memo.id === this.$route.params.id)
    }
  },
  emits: ['editButtonClick', 'deleteButtonClick'],
  methods: {
    editButtonClick () {
      this.$emit('editButtonClick', this.memo.content)
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
