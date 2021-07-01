!<template>
  <main class="content">
      <section class="top-card">
      <img :src="singleContact.avatar" alt="user picture">
      <div class="name">
        <p>{{ singleContact.name }}</p>
      </div>
    </section>

    <section class="middle-card">
      <h2>About</h2>
      <p>{{ singleContact.about }}</p>
    </section>

    <footer>
      <h2>Contact</h2>
      <a href="#" class="contact"><strong>Email : </strong> {{ singleContact.email }}</a>
      <a href="#" class="contact"><strong>Address: </strong>{{ singleContact.address }}</a>
      <a href="#" class="contact"><strong>Gender: </strong>{{ singleContact.gender }}</a>
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
    margin: 50px auto 50px 750px;
}

.top-card {
    width: 100%;
    /* height: 200px; */
}

.top-card img {
    margin-top: 14px;
    width: 100%;
}


.top-card .name {
    width: 50%;
    height: 0;
    text-align: center;
    float: right;
    color:black;
}

.top-card .name p {
    position: relative;
    font-size: 50px;
    font-weight: 800;
    color:white;
    opacity: 1;
    bottom: 140px;
    line-height: 50px;
    text-align: center;
}

.top-card .name span {
    font-weight: 600;
    text-align: center;
    text-transform: uppercase;
}

h2 {
    font-size: 20px;
    color: #000;
    font-weight: 600;
    margin: 12px 0;
    border-bottom: 4px solid rgba(1, 106, 175, 0.603);
    width: 10%;
}

.middle-card, footer {
    margin: 5px 25px 14px;
}

.middle-card {
    text-align: justify;
}
.contact{
    display: block;
    padding-top: 10px;
    pointer-events: none;
    color:black;
    text-decoration: none;

}
footer {
    text-align: left;
}


.content {
  padding: 1px 16px;
}
@media screen and (max-width: 1250px) {
  .content {
      margin-left: 650px;
      width: 400px;
    }
  .top-card .name p {
      left: -50px;
      top: -100px;
      font-size: 47px;
      font-weight: 700;
    }
}

@media screen and (max-width: 1050px) {
  .content {
      margin-left: 605px;
      width: 320px;
    }
  .top-card .name p {
      left: -57px;
      top: -103px;
      font-size: 44px;
      font-weight: 650;
    }
}
@media screen and (max-width: 925px) {
  .content {
      margin-left: 550px;
      width: 300px;
    }
   .top-card .name p {
      left: -38px;
      top: -102px;
      font-size: 40px;
      font-weight: 640;
    }
}
@media screen and (max-width: 860px) {
  .content {
      margin-left: 500px;
      width: 300px;
    }
   .top-card .name p {
      left: -72px;
      top: -103px;
      font-size: 47px;
      font-weight: 700;
    }
}
@media screen and (max-width: 800px) {
  .content {
      margin-left: auto;
    }
}
</style>