<template id="app">
  <Tree :data="menuList" nodeKey="value" labelKey="title" @node-click="handleNodeClick" />
</template>
<script>
import {defineComponent, reactive} from 'vue'
import Tree from '@/components/Tree'
    export default defineComponent({
        components:{
          Tree
        },
        setup(){
            const menuList = reactive([
                    {
                      title:'菜单1',
                      value: '1',
                      children:[
                          {
                              title:'菜单1-1',
                              value: '1-1',
                              children:[
                                  {title:'菜单1-1-1',value: '1-1-1',},
                                  {title:'菜单1-1-2',value: '1-1-2',},
                                  {title:'菜单1-1-3',value: '1-1-3',}
                              ]
                          },
                          {title:'菜单1-2',value: '1-2',},
                          {title:'菜单1-3',value: '1-3',}
                      ]
                    },
                    {
                      title:'菜单2',
                      value: '2',
                      children:[
                          {
                              title:'菜单2-1',
                             value: '2-1',
                              children:[
                                  {title:'菜单2-1-1',value: '2-1-1',},
                                  {title:'菜单2-1-2',value: '2-1-2',},
                              ]
                          },
                        ]
                      },
                    {title:'菜单3', value: '3'}
                ])
            function handleNodeClick(clickItem) {
                console.log(clickItem)
            }
            return {
                handleNodeClick,
                menuList
            }
        },
        
      
    })
</script>

<style scoped>
    html,
    body{
        height: 100%;
        widows: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
    }
</style>
