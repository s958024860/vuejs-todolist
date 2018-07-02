<template xmlns:v-model="http://www.w3.org/1999/xhtml" xmlns:vaild-v-model="http://www.w3.org/1999/xhtml">
  <div>
    <div>
      <input v-model="inputValue"/>
      <button @click="handlerSubmit">提交</button>
    </div>
    <ul>
      <!--<li v-for="(item, index) of list" :key="index">{{item}}</li>-->
      <to-do-item
        v-for="item in list"
        :key="item.id"
        :content="item"
        :index="item.id"
        @delete-father="delete_father"
      ></to-do-item>
    </ul>
    <!--<div id="test-box" v-on:click.stop="testBox">-->
      <!--dfsd-->
    <!--</div>-->
    <!--<input type="checkbox" id="checkbox" v-model="checked"/>-->
    <!--<label for="checkbox">{{ checked }}</label>-->
    <div id='example-3'>
      <input type="checkbox" id="jack" value="Jack" v-model="checkedNames">
      <label for="jack">Jack</label>
      <input type="checkbox" id="john" value="John" v-model="checkedNames">
      <label for="john">John</label>
      <input type="checkbox" id="mike" value="Mike" v-model="checkedNames">
      <label for="mike">Mike</label>
      <br>
      <span>Checked names: {{ checkedNames }}</span>
    </div>
    <div id="example-4">
      <input type="radio" id="one" value="One" name="picked" v-model="picked">
      <label for="one">One</label>
      <br>
      <input type="radio" id="two" value="Two" name="picked" v-model="picked">
      <label for="two">Two</label>
      <br>
      <span>Picked: {{ picked }}</span>
    </div>
    <div id="example-5">
      <select value="heihei" v-model="selected">
        <option>A</option>
        <option>B</option>
        <option>C</option>
      </select>
      <span>selected： {{selected}}</span>
    </div>
    <div id="example-6">
      <select name="" id="" multiple v-model="selectMultiple">
        <option value="1">A</option>
        <option value="2">B</option>
        <option value="3">C</option>
      </select>
      <span>selectMultiple: {{selectMultiple}}</span>
    </div>
    <select v-model="selected">
      <option v-for="option in options" :key="option.id" v-bind:value="option.value">
        {{ option.text }}
      </option>
    </select>
    <span>Selected: {{ selected }}</span>
    <!--<tab-home></tab-home>-->
    <tab-change></tab-change>
  </div>
</template>

<script>
import ToDoItem from './components/ToDoItem.vue'
import TabChange from './components/TabChange.vue'
import TabHome from './components/TabHome.vue'
export default {
  components: {
    'to-do-item': ToDoItem,
    'tab-change': TabChange,
    'tab-home': TabHome
  },
  data: function () {
    return {
      inputValue: '',
      list: [],
      checked: true,
      checkedNames: [],
      picked: '',
      selected: '',
      selectMultiple: [],
      options: [
        { text: 'One', value: 'A' },
        { text: 'Two', value: 'B' },
        { text: 'Three', value: 'C' }
      ]
    }
  },
  methods: {
    handlerSubmit: function () {
      this.list.push(this.inputValue)
      this.inputValue = ''
    },
    delete_father: function (index) {
      this.list.splice(index, 1)
    },
    testBox: function () {
      alert('sdfl')
    }
  }
}
</script>

<style>
  #test-box{
    width: 30px;
    height: 20px;
    background: #eee;
  }
</style>
