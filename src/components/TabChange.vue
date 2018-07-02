<template>
  <div class="demo">
    <button
      v-for="tab in tabs"
      v-on:click="currentTab = tab"
      v-bind:class="['tab-button', { active: currentTab === tab }]"
      v-bind:key="tab.id">
      {{tab}}
    </button>
    <!--<tab-home></tab-home>-->
    <component v-bind:is="currentTabComponent"
               class="tab"></component>
  </div>
</template>

<script>
import TabHome from './TabHome.vue'
import TabPosts from './TabPosts.vue'
import TabArchive from './TabArchive.vue'
export default {
  components: {
    'tab-home': TabHome,
    'tab-posts': TabPosts,
    'tab-archive': TabArchive
  },
  data: function () {
    return {
      currentTab: 'Home',
      tabs: ['Home', 'Posts', 'Archive']
    }
  },
  methods: {
    delete_child: function () {
      this.$emit('delete', this.index)
    }
  },
  computed: {
    currentTabComponent: function () {
      return 'tab-' + this.currentTab.toLowerCase()
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .tab-button {
    padding: 6px 10px;
    border-top-left-radius: 3px;
    border-top-right-radius: 3px;
    border: 1px solid #ccc;
    cursor: pointer;
    background: #f0f0f0;
    margin-bottom: -1px;
    margin-right: -1px;
  }
  .tab-button:hover {
    background: #e0e0e0;
  }
  .tab-button.active {
    background: #e0e0e0;
  }
  .tab {
    border: 1px solid #ccc;
    padding: 10px;
  }
</style>
