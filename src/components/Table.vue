<script lang="ts">
    import DataTable from 'datatables.net-vue3';
    import DataTablesCore from 'datatables.net';
    DataTable.use(DataTablesCore);

    let columnDef:any[] = [{ name: 'column1', style: 'regular'}, {name: 'column2', style: 'red'}];
    let columns:any[] = [];
    for (let column of columnDef) {
        columns.push({
            name: column.name,
            data: column.name,
            title: column.name,
            className: column.style
        });
    }

    export default {
        components: {
            DataTable,
        },
        data() {
            return {
                columns: columns,
                data: [{
                    column1: "value 1",
                    column2: "value 1",
                    column3: "value 1",
                },
                {
                    column1: "value 2",
                    column2: "value 2",
                    column3: "value 2",
                },
                {
                    column1: "value 3",
                    column2: "value 3",
                    column3: "value 3",
                },
                {
                    column1: "value 4",
                    column2: "value 4",
                    column3: "value 4",
                },]
            }
        }
    }
</script>

<template>
    <DataTable :data="data" :columns="columns">
    </DataTable>
</template>

<style lang="scss">
    .odd {
        .regular {
            background-color: #333;
            color: #fafafa;
        }

        .red {
            background-color: #fafafa;
            color: #f00;
        };
    }
    .regular {
        background-color: #fafafa;
        color: #333;
    }
    .red {
        background-color: #f00;
        color: #fafafa;
    }
</style>