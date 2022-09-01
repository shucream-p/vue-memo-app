<template>
  <div>
    <MemoList :memos="memos"/>
    <div>
      <textarea cols="40" rows="15" v-model="newMemo" ref="textarea"></textarea>
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
  emits: ['addButtonClick'],
  data () {
    return {
      newMemo: ''
    }
  },
  mounted () {
    this.$refs.textarea.focus()
  },
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
