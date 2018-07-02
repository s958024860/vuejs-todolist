<template>
  <li class="item" @click="delete_child">{{content}}</li>
</template>

<script>
export default {
  props: ['content', 'index'],
  methods: {
    delete_child: function () {
      this.$emit('delete-father', this.index)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .item{
    color: red;
  }
</style>
