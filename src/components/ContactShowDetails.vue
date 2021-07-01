!<template>
  <main class="content">
      <section class="top-card">
      <img :src="singleContact.avatar" alt="user picture">
      <div class="name">
        <p>{{ singleContact.name }}</p>
      </div>
    </section>

    <section class="middle-card">
      <h1>About</h1>
      <p>{{ singleContact.about }}</p>
    </section>

    <footer>
      <h1>Contact</h1>
      <a href="#" class="contact">Email : {{ singleContact.email }}</a><br>
      <a href="#" class="contact">Address: {{ singleContact.address }}</a><br>
      <a href="#" class="contact">Gender: {{ singleContact.gender }}</a><br>
    </footer>
  </main>
</template>

<script>
export default {
    name:'ContactShowDetails',
    props:{
        singleContact:Object,
    },
    mounted(){
        console.log("Show Details Mounted",this.singleContact);
        // this.forceRerender(this.singleContact);
    }
}
</script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    /* background-color: #EA9684; */
    font-family: Arial, Helvetica, sans-serif;
    background: rgb(255,154,158);
    background: linear-gradient(13deg, rgba(255,154,158,1) 0%, rgba(250,208,196,1) 100%);
}

main {
    width: 500px;
    overflow: hidden;
    background-color: #f1f1f1;
    font-size: 16px;
    line-height: 22px;
    color: #000;
    border-radius: 7px;
    box-shadow: -5px -5px 25px rgba(0, 0, 0, 0.705);
    margin: 50px auto 50px 800px;
}

.top-card {
    width: 100%;
    /* height: 200px; */
}

.top-card img {
    width: 100%;
}

.top-card .menu-icon {
    position: relative;
    width: 22px;
    bottom: 13.7em;
    left: 1.1em;
    cursor: pointer;
}

.top-card .menu-icon .menu {
    position: relative;
    display: block;
    width: 100%;
    height: 4px;
    background-color: #000;
    margin-bottom: 6px;
    opacity: .5;
    transition: .4s;
}

.top-card .menu-icon .item1 {
    left: -5px;
}

.top-card .menu-icon .item2 {
    left: 5px;
}

.top-card .menu-icon:hover .menu {
    left: 0;
    border-radius: 1px;
}

.top-card .name {
    width: 50%;
    height: 0;
    text-align: center;
    float: right;
}

.top-card .name p {
    position: relative;
    font-size: 50px;
    font-weight: 800;
    color: #000;
    opacity: .5;
    bottom: 140px;
    line-height: 50px;
    text-align: center;
}

.top-card .name span {
    font-weight: 600;
    text-align: center;
    text-transform: uppercase;
}

h1 {
    font-size: 20px;
    color: #000;
    font-weight: 600;
    margin: 12px 0;
    border-bottom: 4px solid rgba(1, 106, 175, 0.603);
    width: 10%;
}

.middle-card, footer {
    margin: 5px 25px;
}

.middle-card {
    text-align: justify;
}
.contact{
    color:black;
    text-decoration: none;
}
footer {
    text-align: center;
}


.content {
  padding: 1px 16px;
}
@media screen and (max-width: 550px) {
  .content {margin-left: 100px !important;}
}
@media screen and (max-width: 800px) {
  .content {margin-left: 250px !important;}
}

@media screen and (max-width: 1200px) {
  .content {
      margin-left: 600px;
    }
}

@media screen and (max-width: 1000px) {
  .content {
      margin-left: 500px;
      width: 300px;
    }
}

</style>