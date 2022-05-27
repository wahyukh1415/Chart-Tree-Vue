<template>
    <li :class="[isFolder ? 'folder' :'user']">
    <label
      :class="{'open': open}"
      @click="toggle"
      @dblclick="changeType(model.id)">
      <i v-show="model !== null"></i> {{ model.name }}
      <span v-if="isFolder"> {{ isFolder ? model.children.length : '' }} </span>
      <hr>
    </label>
    <ul v-show="open" v-if="isFolder" :class="{'open': open}">
      <TreeView
        v-for="(model, index) in model.children"
        v-bind:key="index"
        :model="model">
      </TreeView>
    </ul>
  </li>
</template>

<script>
import Vue from 'vue'

export default {
    name: 'TreeView',
    props: {
    model: {}
  },
  data: function() {
    return {
      open: false
    };
  },
  computed: {
    isFolder: function() {
      return this.model.children && this.model.children.length;
    }
  },
  methods: {
    toggle: function() {
      if (this.isFolder) {
        this.open = !this.open;
      }
    },
    changeType: function(data) {
      console.log('id', data)
      const id = data
        // this.$router.push('/editPosisi/' + id)
      // if (!this.isFolder) {
      //   Vue.set(this.model, "children", []);
      //   this.addChild();
      //   this.open = true;
      // }
    },
    addChild: function() {
      this.model.children.push({
        nama: "New Item"
      });
    }
  }
}
</script>

<style scoped lang="scss">
    *, *::after, *::before {
    box-sizing: border-box;
    }

    body {
    color: #fff;
    background: #949c4e;
    background: linear-gradient(
        115deg,
        rgba(86, 216, 228, 1) 10%,
        rgba(159, 1, 234, 1) 90%
    );
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
        Oxygen-Sans, Ubuntu, Cantarell, "Helvetica Neue", Helvetica, Arial,
        sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    overflow: hidden;
    }

    html,
    body,
    .container {
    min-height: 100vh;
    }

    .center {
    display: flex;
    justify-content: center;
    align-items: center;
    }

    ol, ul {
        list-style: none;
        padding: 0px;
    }

    a {
    color: #a0f6aa;
    text-decoration: none;
    }

    h1 {
    text-align: center;
    width: 90%;
    margin: 2em auto 0;
    color: #507b55;
    font-weight: bold;
    }

    .cd-accordion-menu {
    width: 90%;
    max-width: 600px;
    margin: 4em auto;
        background: rgba(0, 0, 0, 0.8);
    box-shadow: 0 4px 6px 0 rgba(0, 0, 0, 0.3);
    }

    .cd-accordion-menu li {
    user-select: none;
    }

    .cd-accordion-menu li span {
      float: right;
    }

    .cd-accordion-menu label, .cd-accordion-menu a {
    text-align: left;
    position: relative;
    display: block;
    padding: 5px 5px 5px 45px;
    // box-shadow: inset 0 -1px #000;
    color: #ffffff;
    color:#73818f;
    }
    .no-touch .cd-accordion-menu label:hover,
    .no-touch .cd-accordion-menu a:hover {
    background: #52565d;
    }
    .cd-accordion-menu label::before,
    .cd-accordion-menu label::after,
    .cd-accordion-menu a::after {
    /* icons */
    content: '';
    display: inline-block;
    width: 16px;
    height: 16px;
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    }
    .cd-accordion-menu label {
    cursor: pointer;
    }

    .cd-accordion-menu label span {
    float: right;
    color: #828282;
    }

    .cd-accordion-menu li.file > label::before {
    content: "\f15b";  
    }
    .cd-accordion-menu li.folder > label::before {
    content: "\f054";
    }

    .cd-accordion-menu li.file > label::before {
    content: "\f15b";  
    }
    .cd-accordion-menu li.add > label::before {
    content: "\f067";
    }


    .cd-accordion-menu label::before {
    /* arrow icon */
    font: normal normal normal 14px/1 FontAwesome;
    left: 18px;
    transform: translateY(-50%);
    transition: transform 0.3s;
    }
    .cd-accordion-menu label.open::before {
    transform: translateY(-25%) rotate(90deg);
    }

    .cd-accordion-menu ul label,
    .cd-accordion-menu ul a {
    // background: #000;
    // box-shadow: inset 0 -1px #141617;
    padding-left: 82px;
    }
    .no-touch .cd-accordion-menu ul label:hover,
    .no-touch .cd-accordion-menu ul a:hover {
    background: #3c3f45;
    }
    .cd-accordion-menu > li:last-of-type > label,
    .cd-accordion-menu > li:last-of-type > a,
    .cd-accordion-menu > li > ul > li:last-of-type label,
    .cd-accordion-menu > li > ul > li:last-of-type a {
    box-shadow: none;
    }
    .cd-accordion-menu ul label::before {
    left: 36px;
    }
    .cd-accordion-menu ul label::after,
    .cd-accordion-menu ul a::after {
    left: 59px;
    }
    //level 3
    .cd-accordion-menu ul ul label,
    .cd-accordion-menu ul ul a {
    padding-left: 100px;
    }
    .cd-accordion-menu ul ul label::before {
    left: 54px;
    }
    .cd-accordion-menu ul ul label::after,
    .cd-accordion-menu ul ul a::after {
    left: 77px;
    }
    //level 4
    .cd-accordion-menu ul ul ul label,
    .cd-accordion-menu ul ul ul a {
    padding-left: 118px;
    }
    .cd-accordion-menu ul ul ul label::before {
    left: 72px;
    }
    .cd-accordion-menu ul ul ul label::after,
    .cd-accordion-menu ul ul ul a::after {
    left: 95px;
    }
    //level 5
    .cd-accordion-menu ul ul ul ul label,
    .cd-accordion-menu ul ul ul ul a {
    padding-left: 136px;
    }
    .cd-accordion-menu ul ul ul ul label::before {
    left: 90px;
    }
    .cd-accordion-menu ul ul ul ul label::after,
    .cd-accordion-menu ul ul ul ul a::after {
    left: 113px;
    }
    //level 6
    .cd-accordion-menu ul ul ul ul ul label,
    .cd-accordion-menu ul ul ul ul ul a {
    padding-left: 154px;
    }
    .cd-accordion-menu ul ul ul ul ul label::before {
    left: 108px;
    }
    .cd-accordion-menu ul ul ul ul ul label::after,
    .cd-accordion-menu ul ul ul ul ul a::after {
    left: 131px;
    }
    //level 7
    .cd-accordion-menu ul ul ul ul ul ul label,
    .cd-accordion-menu ul ul ul ul ul ul a {
    padding-left: 172px;
    }
    .cd-accordion-menu ul ul ul ul ul ul label::before {
    left: 126px;
    }
    .cd-accordion-menu ul ul ul ul ul ul label::after,
    .cd-accordion-menu ul ul ul ul ul ul a::after {
    left: 149px;
    }
    //level 8
    .cd-accordion-menu ul ul ul ul ul ul ul label,
    .cd-accordion-menu ul ul ul ul ul ul ul a {
    padding-left: 190px;
    }
    .cd-accordion-menu ul ul ul ul ul ul ul label::before {
    left: 144px;
    }
    .cd-accordion-menu ul ul ul ul ul ul ul label::after,
    .cd-accordion-menu ul ul ul ul ul ul ul a::after {
    left: 167px;
    }
    //level 9
    .cd-accordion-menu ul ul ul ul ul ul ul ul label,
    .cd-accordion-menu ul ul ul ul ul ul ul ul a {
    padding-left: 208px;
    }
    .cd-accordion-menu ul ul ul ul ul ul ul ul label::before {
    left: 162px;
    }
    .cd-accordion-menu ul ul ul ul ul ul ul ul label::after,
    .cd-accordion-menu ul ul ul ul ul ul ul ul a::after {
    left: 185px;
    }
    //level 10
    .cd-accordion-menu ul ul ul ul ul ul ul ul ul label,
    .cd-accordion-menu ul ul ul ul ul ul ul ul ul a {
    padding-left: 226px;
    }
    .cd-accordion-menu ul ul ul ul ul ul ul ul ul label::before {
    left: 180px;
    }
    .cd-accordion-menu ul ul ul ul ul ul ul ul ul label::after,
    .cd-accordion-menu ul ul ul ul ul ul ul ul ul a::after {
    left: 203px;
    }
</style>