<script>
import BurgerForm from "../components/BurgerForm.vue";

export default {
  components: {
    BurgerForm
  }
}

</script>

<template>
  <section class="hero">
    <div class="container">
      <h1>Welcome to Make Your Burger</h1>
    </div>
  </section>
  <main class="container">
    <BurgerForm />
  </main>
</template>

<style scoped>

  .hero{
    background-image: url('/img/burger.jpg');
    background-size: cover;
    background-position: center;
    color: #ffe83d;
    display:  flex;
    flex-direction: column;
    justify-content: center;
    font-size: 30px;
    height: 500px;
  }

  .container{
    width: 100%;
  }

</style>
