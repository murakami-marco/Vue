<script lang="ts">
    // import DataTable from 'datatables.net-vue3';
    // import DataTablesCore from 'datatables.net';
    import draggable from 'vuedraggable'
    // DataTable.use(DataTablesCore);

    const columnDef:any[] = [{ name: 'ID', style: 'regular'}, {name: 'NOMBRE', style: 'red'}, {name: 'APELLIDO', style: 'blue'}];
    const columns: any[] = [
      {
        ID: "1",
        NOMBRE: "John",
        APELLIDO: "Doe",
      },
      {
        ID: "2",
        NOMBRE: "Jane",
        APELLIDO: "Doe",
      },
      {
        ID: "3",
        NOMBRE: "Luke",
        APELLIDO: "Skywalker",
      },
      {
        ID: "4",
        NOMBRE: "Leia",
        APELLIDO: "Organa",
      },
    ];
    const headers:string[] = columnDef.map(header => header.name)

    export default {
    components: {
            draggable,
            // DataTable,
        },
        data() {
            return {
                headers,
                list: columns,
                dragging: false
            }
        }
    }
</script>

<template>
    <!-- <DataTable :data="data" :columns="columns">
    </DataTable> -->

    <div class="row">
    <div class="col-8">
      <h3>Draggable table</h3>

      <table class="table table-striped">
        <thead class="thead-dark">
          <draggable v-model="headers" tag="tr" :item-key="(key: any) => key">
            <template #item="{ element: header }">
              <th scope="col">
                {{ header }}
              </th>
            </template>
          </draggable>
        </thead>
        <tbody>
          <tr v-for="item in list" :key="item.name">
            <td v-for="header in headers" :key="header">{{ item[header] }}</td>
          </tr>
        </tbody>
      </table>
    </div>

    <rawDisplayer class="col-2" :value="list" title="List" />

    <rawDisplayer class="col-2" :value="headers" title="Headers" />
  </div>
</template>

<style lang="scss">
    .table {
        width: 100%;
        margin-bottom: 1rem;
        color: #212529;
    }
    .odd {
        .regular {
            background-color: #333;
            color: #fafafa;
        }
        .red {
            background-color: #fafafa;
            color: #f00;
        };
        .blue {
            background-color: #fafafa;
            color: rgb(0, 94, 255);
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
    .blue {
        background-color: rgb(0, 94, 255);
        color: #fafafa;
    }
</style>