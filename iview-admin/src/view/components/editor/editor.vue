<template>
  <div>
    <editor ref="editor" :value="content" @on-change="handleChange"/>
    <Button @click="changeContent">修改编辑器内容</Button>
  </div>
</template>

<script>
import Editor from '_c/editor'
export default {
  name: 'editor_page',
  components: {
    Editor
  },
  data () {
    return {
      content: ''
    }
  },
  methods: {
    handleChange (html, text) {
      console.log(html, text)
    },
    changeContent () {
      this.$refs.editor.setHtml('<p>powered by wangeditor</p>')//修改编辑器内容触发
    }
  }
}
</script>

<style>

</style>
