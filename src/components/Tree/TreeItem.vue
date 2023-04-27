<template>
    <div>
        <div :class="{ 'active-node': item[nodeKey] === activeId, 'tree-item-label': true }" @click="clickNode" ref="curDom">
            <span>{{item[labelKey]}} </span>
            <span v-if="item.children && item.children.length !== 0">&gt;</span>
        </div>
        <div v-if="isExpand && item.children && item.children.length > 0" class="tree-sub-item">
            <TreeItem v-for="(item) in item.children" :key="item[nodeKey]" :item='item' :activeId="activeId" @getClickNode='getClickNode' :nodeKey="nodeKey" :labelKey="labelKey"></TreeItem>
        </div>
    </div>
</template>

<script>
import {defineComponent,ref} from 'vue'

export default defineComponent({
    name: 'TreeItem',
    props:{
        item:{
            default:() => {},
            type:Object
        },
        activeId: String,
        nodeKey: String,
        labelKey: {
            default: 'label',
            type: String
        }
       
    },
    setup(props,{emit}) {
        let isExpand = ref(false)
        let curDom = ref()
        function clickNode(){
            isExpand.value = !isExpand.value
            emit('getClickNode',props.item)
        }
        function getClickNode(item) {
            emit('getClickNode', item)
        }
       
        return {
            isExpand,
            clickNode,
            getClickNode,
            curDom,
        }
    }
});
</script>

<style scoped>
    .tree-item-label{
        line-height: 2em;
    }
    .active-node {
        background-color: #eee;
    }
    .tree-sub-item {
        padding-left: 20px;
    }
</style>