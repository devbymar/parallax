<template>
  <div class="body">
    <div class="container">
      <div class="card">
        <div class="content" style="color: black;">
          <h2>01</h2>
          <h3>Card One</h3>
          <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolores vero eveniet, debitis nemo tempora dolorem quisquam quis mollitia natus dolorum minima aperiam laborum maxime iure inventore facere maiores. Tempora, repellat.</p>
          <a href="#">Read more</a>
        </div>
      </div>
      <div class="card">
        <div class="content" style="color: black;">
          <h2>02</h2>
          <h3>Card Two</h3>
          <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolores vero eveniet, debitis nemo tempora dolorem quisquam quis mollitia natus dolorum minima aperiam laborum maxime iure inventore facere maiores. Tempora, repellat.</p>
          <a href="#">Read more</a>
        </div>
      </div>
      <div class="card">
        <div class="content" style="color: black;">
          <h2>03</h2>
          <h3>Card Three</h3>
          <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolores vero eveniet, debitis nemo tempora dolorem quisquam quis mollitia natus dolorum minima aperiam laborum maxime iure inventore facere maiores. Tempora, repellat.</p>
          <a href="#">Read more</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { VanillaTilt } from "../vanillatilt";

export default {
  mounted() {
    // Selecciona todas las tarjetas con la clase 'card'
    const cards = this.$el.querySelectorAll('.card');
    // Inicializa VanillaTilt para cada tarjeta
    cards.forEach(card => {
      VanillaTilt.init(card, {
        max: 25,
        speed: 400,
        glare: true,
        "max-glare": 1,
      });
    });
  }
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css?family=Poppins:400,500,600,700,800,900&display=swap');

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
  background: #161623;
}

.body::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(#f00, #f0f);
  clip-path: circle(30% at right 70%);
}

.body::after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(#2196f3, #e91e63);
  clip-path: circle(30% at 10% 10%);
}

.container {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  max-width: 1200px;
  flex-wrap: wrap;
  z-index: 1;
}

.container .card {
  position: relative;
  width: 280px;
  height: 400px;
  margin: 30px;
  box-shadow: 20px 20px 50px rgba(0, 0, 0, 0.5);
  border-radius: 15px;
  background: rgba(255, 255, 255, 0.1);
  overflow: hidden;
  display: flex;
  justify-content: center;
  align-items: center;
  border-top: 1px solid rgba(255, 255, 255, 0.5);
  border-left: 1px solid rgba(255, 255, 255, 0.5);
  backdrop-filter: blur(5px);
}

.container .card .content {
  padding: 20px;
  text-align: center;
  transform: translateY(100px);
  opacity: 0;
  transition: 0.5s;
}

.container .card:hover .content {
  transform: translateY(0px);
  opacity: 1;
}

.container .card .content h2 {
  position: absolute;
  top: -30px;
  right: 30px;
  font-size: 8em;
  color: rgba(255, 255, 255, 0.05);
  pointer-events: none;
}

.container .card .content h3 {
  font-size: 1.8em;
  color: #fff;
  z-index: 1;
  padding-top: 50px;
}

.container .card .content p {
  font-size: 1em;
  color: #fff;
  font-weight: 300;
  padding-top: 10px;
}

.container .card .content a {
  position: relative;
  display: inline-block;
  padding: 8px 20px;
  margin-bottom: 15px;
  background: #fff;
  color: #000;
  border-radius: 20px;
  text-decoration: none;
  font-weight: 500;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.5);
}
</style>
