<template>
  <div>
    <MemoList :memos="memos"/>
    <div>
      <textarea cols="40" rows="15" v-model="newMemo"></textarea>
    </div>
    <div>
      <button @click="addButtonClick">保存</button>
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
  props: {
    memos: Array
  },
  data () {
    return {
      newMemo: ''
    }
  },
  emits: ['addButtonClick'],
  methods: {
    addButtonClick () {
      this.$emit('addButtonClick', this.newMemo)
    }
  }
}
</script>

<style scoped>
  textarea {
    margin-bottom: 20px;
  }
</style>
