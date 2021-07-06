<template>
 <div>
 <app-sidebar :data="data" @event='addEdit' ></app-sidebar>
 <app-table :items="items" @delete="edit" @edit="deleterow"></app-table>
 </div>
</template>

<script>

import Table from '@/components/Table.vue';
import SideBar from '@/components/SideBar.vue';
  export default {
    data() {
    return {
        items: [
          { age: 40, first_name: 'Jagadeesh', last_name: 'Kuna', },
          { age: 21, first_name: 'Rahul', last_name: 'Vangari', },
          { age: 66, first_name: 'Nikhil', last_name: 'Reddy', },
        ],
        data:[]
      }
    },
    components: {
      'app-sidebar':SideBar,
      'app-table': Table
    },

    methods: {
      addEdit(age,fname,lname,index) {
        if(index == null){
          this.items.push({age: age, first_name: fname, last_name: lname});
        }else{
          this.items.splice(index, 1,{age: age, first_name: fname, last_name: lname});
        }
      },
      edit(row){
            this.data = row
        },
      deleterow(row){
             if(confirm("Do you really want to delete?")){
                    this.items.splice(row['index'], 1);
             }

      },
    }
  }
</script>
