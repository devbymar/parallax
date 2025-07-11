<template>
  <div class="body">
    <div class="container">
      <div class="card">
        <div class="imgBx">
          <img :src="props.cover_image" alt="">
        </div>
        <div class="content">
          <div>
            <h3>{{ props.title }}</h3>
            <h6>{{ props.price }} - {{ props.isbn }}</h6>
            <p>{{ props.description }}</p>
            <a :href="props.url">Read more</a>
          </div>
        </div>
      </div>

    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  title: String,
  price: String,
  isbn: String,
  description: String,
  cover_image: String,
  url: String
})
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css?family=Poppins:400,500,600,700,800,900&display=swap');
/*
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Poppins', sans-serif;
}


.body {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background: linear-gradient(0deg, #b8ff2e, #2ea8ff);
  background-attachment: fixed;
}
*/

.container {
  position: relative;
  width: 1000px;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  margin: 20px;
  padding: 20px 0;
  color: black;
}

.container .card {
  position: relative;
  height: 375px;
  background: #fff;
  widows: 45%;
  margin: 30px 30px;
  border-radius: 20px;
  box-shadow: 0.5px 15px rgba(0, 0, 0, 0.1);
  /*max-width: 375px;*/
}

.container .card .imgBx {
  position: absolute;
  top: 10px;
  left: 10px;
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(20px);
  height: calc(100% - 20px);
  width: calc(100% - 20px);
  z-index: 1;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
  border-radius: 20px;
  border: 1px solid rgba(255, 255, 255, 0.2);
  box-shadow: 5px 5px 30px rgba(0, 0, 0, 0.1);
  transition: 0.5 ease-in-out;
}

.container .card:hover .imgBx {
  height: 150px;
  width: 150px;
  left: -75px;
  top: calc(50% - 75px);
}

.container .card .imgBx img {
  max-width: 350px;
  filter: invert(1);
  transition: 0.5 ease-in-out;
}

.container .card:hover .imgBx img {
  max-width: 75px;
}

.container .card .content {
  /*position: absolute;*/
  right: 0;
  width: calc(100% - 75px);
  max-width: 375px;
  height: 100%;
  min-height: 375px;
  padding: 40px 0px 40px 75px;
  display: flex;
  justify-content: center;
  align-items: center;
  /*margin-left: 70px;*/
}

.container .card .content h3 {
  color: #ff0057;
  margin-bottom: 15px;
  font-size: 24px;
  font-weight: bold;
}

.container .card .content a {
  display: inline-block;
  margin-top: 10px;
  padding: 8px 20px;
  border-radius: 5px;
  background: #0095ff;
  text-decoration: none;
  color: #fff;
  font-weight: 500;
}

@media (max-width: 992px) {
  .container {
    position:relative;
    width: 100%;
    flex-direction: column;
    align-items: center;
  }

  .container .card {
    width: 300px;
    height: auto;
    flex-direction: column;
    background: transparent;
    margin: -20px 0;
    box-shadow: none;
  }

  .container .card .imgBx {
    position: relative;
  }

  .container .card .imgBx,
  .container .card:hover .imgBx {
    width: 80%;
    height: 200px;
    top: 100px;
    left: 10%;
  }

  .container .card:hover .imgBx {
    top: 80px;
  }

  .container .card .imgBx img,
  .container .card:hover .imgBx img {
    max-width: 100px;
  }

  .container .card .content {
    position: relative;
    width: 100%;
    background: #fff;
    box-shadow: none;
    border-radius: 20px;
    padding: 20px 40px 40px;
    border-top: 100px solid #fff;
  }
}
</style>
