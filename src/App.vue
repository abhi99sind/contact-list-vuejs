<template>
  <div id="app">
    <Header :contacts="contacts" :index="selectedIndex" :hover="hover" @headerClick="dataRecieved($event)"></Header>
    <div class="sidebar">
      <contact-side-bar :contacts="contacts" :index="selectedIndex" :hover="hover" @show="dataRecieved($event)"></contact-side-bar>
    </div>
    <contact-show-details v-if="showDetailsOrNot" :singleContact="singleContact!= null ? singleContact : {name : 'Hello World'}"></contact-show-details>
  </div>
</template>

<script>
import Header from './components/Header.vue';
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
    Header,
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

.sidebar {
  margin: 0;
  padding: 0;
  width: 475px;
  background-color: #f1f1f1;
  position: fixed;
  height: 100%;
  overflow: scroll;
}

@media screen and (max-width: 800px) {
  .sidebar {
    width: 100%;
    height: auto;
    position: relative;
    display: none;
  }
  .sidebar a {float: left;}
}

@media screen and (max-width: 925px) {
  .sidebar {
    width: 50%;
  }
}
</style>
