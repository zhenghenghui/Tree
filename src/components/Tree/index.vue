<template>
    <TreeItem  v-for="(item) in data " :key="item[nodeKey]" :item='item' :activeId="activeId" @getClickNode='getClickNode' :nodeKey="nodeKey" v-bind="$attrs"></TreeItem>
</template>

<script>
import {defineComponent, ref} from 'vue'
import TreeItem from './TreeItem.vue';

export default defineComponent({
    name: 'Tree',
    components:{TreeItem},
    props:{
        data:{
            default:() => [],
            type:Array
        },
        nodeKey: {
            default: 'id',
            type: String
        }
    },
    emits: ['node-click'],
    setup(props,{emit}) {
        let activeId = ref('')
        function getClickNode(item){
            activeId.value = item[props.nodeKey]
            emit('node-click', item)
        }
        return {
            activeId,
            getClickNode
        }
    }
});
</script>
