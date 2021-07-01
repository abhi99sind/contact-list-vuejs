<template>
  <div id="app">
    <nav class="navbar sticky-top navbar-dark bg-dark">
    <b-button class="menu-button" v-b-toggle.sidebar-1><b-icon icon="menu-button-wide"></b-icon></b-button>
    <b-sidebar id="sidebar-1" title="Sidebar" shadow>
      <div class="px-3 py-2">
        <p>
          Cras mattis consectetur purus sit amet fermentum. Cras justo odio, dapibus ac facilisis
          in, egestas eget quam. Morbi leo risus, porta ac consectetur ac, vestibulum at eros.
        </p>
        <b-img src="https://picsum.photos/500/500/?image=54" fluid thumbnail></b-img>
      </div>
    </b-sidebar>
    <a class="navbar-brand">Contact List</a>
    <form class="form-inline my-2 my-lg-0">
      <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
    </form>
    </nav>
    <contact-side-bar :contacts="contacts" :index="selectedIndex" :hover="hover" @show="dataRecieved($event)"></contact-side-bar>
    <contact-show-details v-if="showDetailsOrNot" :singleContact="singleContact!= null ? singleContact : {name : 'Hello World'}"></contact-show-details>
  </div>
</template>

<script>
import ContactSideBar from './components/ContactSideBar.vue';
import ContactShowDetails from './components/ContactShowDetails.vue';
export default {
  name: 'App',
  mounted(){
    this.created();
  },
  components:{
    ContactSideBar,
    ContactShowDetails,
  },
  data(){
    return{
      contacts:[{}],
      hover:false,
      selectedIndex:null,
      singleContact:null,
      showDetailsOrNot:false,
      highlightOrNot:false,
    }
  },
  methods:{
    created(){
      fetch("http://www.json-generator.com/api/json/get/cfjBPIUaPS?indent=2")
      .then(resp => resp.json())
      .then(data => {
        this.contacts = data;
        var index = localStorage.getItem('selectedIndex');
        if(index != null){
          this.selectedIndex = index;
          this.showDetailsOrNot = true;
          this.singleContact = this.contacts.filter(contact => contact.uid == this.selectedIndex);
          this.singleContact = this.singleContact[0];
        }
        // this.singleContact = this.contacts[0];
      })
      .catch(err => console.log(err));
    },
    dataRecieved(contactData){
      console.log("Contact Data",contactData);
      this.singleContact = contactData;
      this.selectedIndex = contactData.uid;
      localStorage.setItem('selectedIndex',this.selectedIndex);
      this.forceRerender(contactData);
    },
    forceRerender(contactData)
    {
      this.singleContact = contactData;
      this.showDetailsOrNot = true;
    }
  }
  
}
</script>

<style>
body{
  margin: 0;
  font-family: "Lato", sans-serif;
}
.menu-button{
  display: none!important;
}
@media screen and (max-width: 600px){
  .menu-button{
    display: block!important;
  }
}
</style>
