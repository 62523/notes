

<script>
import { RouterLink, RouterView } from 'vue-router'
 
import { createApp, ref } from 'https://unpkg.com/vue@3/dist/vue.esm-browser.js'
const API_URL="http://localhost:5024/";
createApp({
    data() {
        return {
            title: "Notes",
            notes:[]
        }
    }, methods:{
      async refreshData(){
          axios.get(API_URL+"api/notes/GetNotes").then(
            (response)=>{
              this.notes=response.data;
            }
          )
      }
    },mounted:function(){
      this.refreshData();
    }
}).mount('#app')
</script>

<template>
  <div>
  <b-navbar type="light" variant="info">
    <b-navbar-nav>
      <a href="/">
      <b-icon-journal-bookmark style="margin-left: 8px; width: 40px; height: 40px; color:black;"></b-icon-journal-bookmark>
    </a>
      <b-nav-item href="/About">
        
        Kalendarz
      </b-nav-item>
      <b-nav-item href="#">Home</b-nav-item>
       
      

      <b-nav-item-dropdown text="User" right>
        <b-dropdown-item href="#">Account</b-dropdown-item>
        <b-dropdown-item href="#">Settings</b-dropdown-item>
      </b-nav-item-dropdown>
      <b-nav-form>
          <b-row class="align-items-center">
            <b-col cols="auto">
              <b-form-input placeholder="Search"></b-form-input>
            </b-col>
            <b-col cols="auto">
              <b-button variant="outline-dark" type="submit">Search</b-button>
            </b-col>
          </b-row>
        </b-nav-form>
    </b-navbar-nav>
  </b-navbar>
</div>

  <RouterView />
</template>

<style scoped>

</style>
