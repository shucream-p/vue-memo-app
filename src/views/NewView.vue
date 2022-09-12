<template>
  <div>
    <MemoList :memos="memos"/>
    <div>
      <textarea cols="40" rows="15" v-model="content" ref="textarea"></textarea>
    </div>
    <div>
      <button @click="createButtonClick">保存</button>
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
  emits: ['createButtonClick'],
  data () {
    return {
      content: ''
    }
  },
  mounted () {
    this.$refs.textarea.focus()
  },
  methods: {
    createButtonClick () {
      this.$emit('createButtonClick', this.content)
    }
  }
}
</script>

<style scoped>
  textarea {
    margin-bottom: 20px;
  }
</style>
