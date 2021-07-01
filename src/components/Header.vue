!<template>
  <nav class="navbar sticky-top navbar-dark bg-dark">
    <b-button class="menu-button" v-b-toggle.sidebar-1><b-icon icon="menu-button-wide"></b-icon></b-button>
    <b-sidebar id="sidebar-1" title="Contacts List" shadow>
      <div class="px-3 py-2">
          <contact-side-bar :contacts="contacts" :index="index" :hover="hover" @show="$emit('headerClick',$event)"></contact-side-bar>
      </div>
    </b-sidebar>
    <a class="navbar-brand">Contact List</a>
    <form class="form-inline my-2 my-lg-0">
      <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
    </form>
    </nav>
</template>

<script>
import ContactSideBar from './ContactSideBar.vue';
export default {
    name:'Header',
    emits:['headerClick'],
    props:{
        contacts: Array,
        hover: Boolean,
        index:String,
    },
    components:{
        ContactSideBar,
    },
    methods:{
      headerClick(headerCon){
        console.log("Header Sidebar Contact Click Eevnt",headerCon);
      }
    }

}
</script>

<style>
.menu-button{
  display: none!important;
}
@media screen and (max-width: 800px){
  .menu-button{
    display: block!important;
  }
}
#sidebar-1{
    width:400px;
}
</style>