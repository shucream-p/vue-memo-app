<template>
<div>
  <div>
    <textarea v-model="memos.find(element => element.id === this.$route.params.id).content"></textarea>
  </div>
  <div>
      <button @click.prevent="editMemo">編集</button>
  </div>
</div>
</template>

<script>
export default {
  data () {
    return {
      memos: JSON.parse(localStorage.getItem('memos'))
    }
  },
  methods: {
    editMemo () {
      localStorage.setItem('memos', JSON.stringify(this.memos))
      this.$router.push('/')
    }
  }
}
</script>
