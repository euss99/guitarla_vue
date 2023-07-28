<template>
  <Header />

  <main class="container-xl mt-5">
    <h2 class="text-center">Nuestra Colección</h2>

    <div class="row mt-5">
      <Guitarra
        v-for="guitarra in guitarras"
        :guitarra="guitarra"
        @agregar-carrito="agregarCarrito"
      />
    </div>
  </main>

  <Footer />
</template>

<script setup>
import Guitarra from "./components/Guitarra.vue";
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";
import { ref, reactive, onMounted } from "vue";
import { db } from "./data/guitarras";

const guitarras = ref([]);
const carrito = ref([]);

const agregarCarrito = (guitarra) => {
  guitarra.cantidad = 1;
  carrito.value.push(guitarra);

  console.log(carrito.value);
};

onMounted(() => {
  guitarras.value = db;
});
</script>

<style scoped></style>
