<script lang="ts">
    import draggable from 'vuedraggable';

    export default {
        components: {draggable},
        data() {
            return {
                drag: false
            };
        },
        computed: {
            myList: () => {
                return [{id: 1, name: 'column1'}, {id: 2, name: 'column2'}];
            }
        }
    }
</script>

<template>
    <draggable v-model="myList" @start="drag=true" @end="drag=false">
        <template #item="{element}" item-key="id">
            <div class="box">{{ element.name }}</div>
        </template>
    </draggable>
    <ul>
        <li v-for="column in myList">{{ column.name }}</li>
    </ul>
</template>

<style lang="scss">
    .box {
        border-color: black;
        width: 200px;
        height: 50px;
        background-color: white;
        color: black;
    }
</style>