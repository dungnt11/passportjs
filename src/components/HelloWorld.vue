<template>
  <div class="hello">
    <h1>Xin chao</h1>
    <p>{{ test }}</p>
    <select id="mon">
      <option v-for="monAn in monAns" :key="monAn"
        :value="monAn"
        :selected="monAn == 'ca ri'"
        >
        {{ monAn }}</option>
    </select>
    <input type="text" @input="name = $event.target.value">
    <p v-hightlight:name.pre.name="{color: 'red', background: 'blue'}">Mon an: {{ name }}</p>
    <p>{{ test | upperCase('showjav') }}</p>
    <hr>
    <input type="text" v-model="searchMonAn">
    <ul>
      <li v-for="monAn in monAnCompud" :key="monAn">{{ monAn }}</li>
    </ul>
    <button @click="show = !show">Click me</button>
    <transition name="fade">
    <div v-if="show">Nội dung show</div>
    </transition>
    <hr>
    <select v-model="typeAnimation">
      <option value="fade">fade</option>
      <option value="slide">slide</option>
    </select>
  </div>
</template>

<script>
import appMixComponent from '@/components/mixComponent'
export default {
  data () {
    return {
      test: this.$store.state.data,
      monAns: ['com ga', 'ca ri', 'bit tet'],
      name: '',
      searchMonAn: '',
      show: true,
      typeAnimation: 'slide'
    }
  },
  directives: {
    hightlight (el, bind, vnode) {
      console.log(bind.value)
      el.style.backgroundColor = bind.value
    }
  },
  filters: {
    upperCase (value, params) {
      return value.toUpperCase()
    }
  },
  computed: {
    monAnCompud () {
      return this.monAns.filter(e => {
        return e.match(this.searchMonAn)
      })
    }
  },
  mixins: [appMixComponent]
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .fade-enter {
    opacity: 0;
  }
  .fade-enter-active {
    animation: hieuUng 1s ease;
  }
  @-webkit-keyframes hieuUng {
    0% { opacity: 0; transform: translateY(-50px) }
    50% { opacity: 1; transform: translateY(0) }
    100% { opacity: 0; transform: translateY(50px) }
  }
</style>
