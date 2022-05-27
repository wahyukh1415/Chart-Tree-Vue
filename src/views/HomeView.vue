<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <h1>Organization Chart</h1>
    <ul class="cd-accordion-menu">
        <TreeView :model="treeData"></TreeView>
    </ul>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import TreeView from '@/components/TreeView.vue'

export default {
  name: 'HomeView',
  components: {
    HelloWorld,
    TreeView
  },
  data: function () {
      return {
        treeData: {
            name: 'Mark Zuckerberg',
            children: [
              { name: 'Sarah Donal',
                children: [
                  {
                    name: 'Cassandra Reynolds',
                    children: [
                      { name: 'Mary Blue' },
                      { name: 'Bob Saget',
                        children: [
                        { name: 'Tina Teff', 
                          children: [
                            {name: 'Will Turner'}
                          ]
                        },
                      ]
                      }
                    ]
                  },
                ]
              },
              {
                name: 'Tyler Simpson',
                children: [
                  {
                    name: 'Harry Tobs',
                    children: [
                      { name: 'Thomas Brown' },
                    ]
                  },
                  { name: 'George Carrey' },
                  { name: 'Gary Styles' },
                ]
              },
              { name: 'Bruce Willis' },
              {
                name: 'Georgina Flangy',
                children: [
                  {
                    name: 'Sophie Turner:',
                  },
                ]
              },
            ]
          },
      }
    },
}
</script>
