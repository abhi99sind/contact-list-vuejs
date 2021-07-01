!<template>
      <div class="container">
        <ul class="cards" :key="contact.uid" v-for="contact in contacts">
            <contact-card :con="contact" :selectedIndex="index" :hoverOrNot="hover" @sendData="$emit('show',$event)"></contact-card>
        </ul>
    </div>
</template>

<script>
import ContactCard from './ContactCard.vue';
export default {
    name:'ContactSideBar',
    components:{
      ContactCard,
    },
    emits:['show'],
    props:{
        contacts: Array,
        hover: Boolean,
        index:String,
    },
    methods:{
      show(con){
        console.log("Show Data",con);
      }
    }
}
</script>

<style scoped>
/* @import url("https://fonts.googleapis.com/css?family=Open+Sans:400,600,700"); */
body {
  font-family: "open sans";
  color: #444;
  font-size: 1em;
}
.container {
  padding: 10px;
}
.clearfloat {
  content: '';
  display: block;
  clear: both;
}

.cards {
  list-style: none;
  margin: 0;
  padding: 0;
  text-align: center;
}

</style>