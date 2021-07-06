<template>
  <div>
    <b-table striped hover :items="items" :fields="fields">
        <template v-slot:cell(actions)="row">
            <b-button @click="edit(row)"> Edit </b-button>
            <b-button @click="deleterow(row)"> Delete </b-button>
        </template>
    </b-table>
  </div>
</template>

<script>
  export default {
     props: ['items'],
      data() {
          return {
            name:"nikil"  ,
            fields: [
                'age',
                'first_name',
                'last_name',
                'actions' 
            ] 
        }
    },
    methods:{
        edit(row){
             this.$emit("delete", row)
        },
        deleterow(row){
             this.$emit("edit", row)
        },
    }
  }
</script>