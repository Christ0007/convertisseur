<script setup>
import { ref, computed } from 'vue'

const taux = 655.957

const fcfa = ref('')
const euro = ref('')

const fcfaToEuro = computed(() => {
  if (!fcfa.value) return ''
  return (Number(fcfa.value) / taux).toFixed(2)
})

const euroToFcfa = computed(() => {
  if (!euro.value) return ''
  return (Number(euro.value) * taux).toFixed(0)
})
</script>

<template>
  <div class="container">
    <h1>Convertisseur FCFA ↔ Euro</h1>

    <div class="card">
      <label>Montant en FCFA</label>
      <input
        type="number"
        v-model="fcfa"
        placeholder="Entrer un montant"
      />

      <p>
        {{ fcfa || 0 }} FCFA =
        <strong>{{ fcfaToEuro || 0 }} €</strong>
      </p>
    </div>

    <div class="card">
      <label>Montant en Euro</label>
      <input
        type="number"
        v-model="euro"
        placeholder="Entrer un montant"
      />

      <p>
        {{ euro || 0 }} € =
        <strong>{{ euroToFcfa || 0 }} FCFA</strong>
      </p>
    </div>
  </div>
</template>

<style>
body {
  font-family: Arial, sans-serif;
  background: #111111;
}

.container {
  max-width: 600px;
  margin: 50px auto;
}

.card {
  background: black;
  padding: 20px;
  margin-bottom: 20px;
  border-radius: 10px;
}

input {
  width: 100%;
  padding: 10px;
  margin: 10px 0;
}

h1 {
  text-align: center;
}
</style>