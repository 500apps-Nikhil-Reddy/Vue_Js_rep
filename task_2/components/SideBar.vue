<template>
  <div>
      <b-button v-b-toggle.sidebar-right>Add Person Details</b-button>
    <!-- <app-table></app-table> -->
    <b-sidebar id="sidebar-right" title="Sidebar" right  v-model="isSidebarOpen">
    <div>
    <b-form @submit.prevent="submit">
        <b-form-group  label="First Name:"></b-form-group>

        <b-form-input v-model="fname" placeholder="Enter your firstname" name="fName"></b-form-input>
        
        

        <b-form-group label="Last Name:"></b-form-group>

        <b-form-input v-model="last_name"  placeholder="Enter your lastname" name="lName"></b-form-input>
        


        <b-form-group label="Age:"></b-form-group>

        <b-form-input v-model="age" placeholder="Enter your age" type ="number"   name="age"></b-form-input>
        
        <br>
        <b-button type="submit" variant="primary">{{ this.buttonText }}</b-button>
        </b-form>
    </div>
    </b-sidebar>
  </div>
</template>

<script>

export default {

    props:['data'],
   data() {
      return {
          index:null,
          fname: '',
          age:'', 
          last_name:'',
          isSidebarOpen: false,
          buttonText : 'Add'
      }
    },
    watch:{
        data:function (val){
            this.isSidebarOpen = true
            this.last_name = val['item']['last_name'],
            this.fname = val['item']['first_name'],
            this.age = val['item']['age'];
            this.index = val['index'];
            this.buttonText = 'Update';
        }
    },
    methods: {
        submit() {
            this.$emit("event", this.age,this.fname,this.last_name,this.index)
            this.fname = ''
            this.age = ''
            this.last_name = ''
            this.index = null
            this.buttonText = 'Add';
            this.isSidebarOpen = false

        }
    }
  }
</script>