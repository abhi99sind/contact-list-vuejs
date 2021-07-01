<template>
    <a @click="$emit('sendData',con)">
        <div class='contact-section' @mouseover="hover  = !hover" @mouseleave="hover = false">
            <li :class="backgroundColor">
                <img :src="con.avatar" />
                <div class="details">
                    <span class="name">{{ con.name }}</span>
                    <span :class="con.status">● {{ con.status }}</span>
                    <a class="phone" v-show="hover">{{ con.phone }}</a>
                    <a class="email" v-show="hover">{{ con.email }}</a>
                </div>
            </li>
        </div>
        
    </a>
  
</template>

<script>
export default {
    name:'ContactCard',
    props:{
        con: Object,
        hoverOrNot: Boolean,
        selectedIndex: String,
    },
    emits:['sendData'],
    data(){
        return {
            hover: this.hoverOrNot,
        }
    },
    computed:{
        backgroundColor(){
            if(this.selectedIndex == this.con.uid)
                return "blue";
            else
                return "";
        }
    }
}
</script>

<style scoped>
.online{
  color: green;
}
.offline{
  color:red;
}
.blue{
    background-color: lightblue;
}
 li {
  margin: 10px;
  padding: 20px;
  border: 1px solid rgba(0, 0, 0, 0.2);
  box-shadow: 0 0 15px rgba(0, 0, 0, 0.5);
  font-size: 0.9em;
  transition: all 0.2s ease-in-out;
  text-align: center;
}
 li:after,
 li:before {
  content: '';
  display: block;
  clear: both;
}
 li img {
  display: inline-block;
  width: 100%;
  height: auto;
  max-width: 100px;
  float: left;
  border-radius: 50%;
  box-shadow: 0 0 2px rgba(0, 0, 0, 0.5);
  transition: all 0.5s ease-in-out;
}
 li .details {
  float: left;
  text-align: left;
  transition: all 0.5s ease-in-out;
  text-shadow: 1px 1px rgba(0, 0, 0, 0);
  min-width: 250px;
}
 li .details > span,
 li .details > a {
  display: block;
  padding: 0 15px 0 35px;
  margin-bottom: 15px;
  text-decoration: none;
  position: relative;
}
 li .details > span:before,
 li .details > a:before {
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin-right: 15px;
  width: 15px;
  text-align: center;
  color: #444;
}
 li .details a {
  color: #57893c;
  transition: color 0.5s ease-in-out;
}

 li .details .name {
  font-weight: 800;
}


 li:hover img {
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.6);
  transition: all 0.4s ease-in-out;
}
 li:hover .details {
  transition: all 0.5s ease-in-out;
  
}
@media (max-width: 550px) {
   li {
    display: block;
    width: auto;
    max-width: 450px;
    margin: 30px auto;
  }
   li img,
   li .details {
    float: none;
  }
   li img {
    margin: 0 auto;
  }
   li .details {
    margin-top: 20px;
    text-align: center;
    min-width: 0;
  }
   li .details span,
   li .details a {
    padding: 0;
    white-space: break-all;
    word-wrap: break-word;
  }
   li .details span:before,
   li .details a:before {
    display: none;
  }
}
.name{
    color:black;
}
@media screen and (max-width: 925px) {
  .details {
    width: 50%;
  }
}
@media screen and (max-width: 870px) {
  .details {
    width: 50%;
    margin-left: 81px;
    margin-top: -96px;
  }
}
</style>