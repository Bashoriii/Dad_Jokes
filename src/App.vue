<template>
  <main>
    <div class="container">
      <div class="card">
        <div class="card-body">
          <h5 v-if="!setup">Click the reload button to get a joke</h5>
          <h5 class="card-title">{{ setup }}</h5>
          <p class="card-text">{{ punchline }}</p>
          <button class="btn-jokes" @click="getJokes">Reload</button>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  data() {
    return {
      setup: "",
      punchline: "",
    };
  },
  methods: {
    async getJokes() {
      const res = await fetch(
        "https://official-joke-api.appspot.com/random_joke"
      );
      const data = await res.json();
      this.setup = data.setup;
      this.punchline = data.punchline;
    },
  },
};
</script>

<style>
body {
  background-color: pink;
}

.container {
  height: 90vh;
  width: 95vw;
  display: flex;
  justify-content: center;
  align-items: center;
}

.card {
  padding: 1.5rem;
  background-color: #fff;
  border: 1px solid #dddddd;
  border-radius: 5px;
  text-align: right;
  max-width: 50vw;
}

.card-body {
  font-size: 1.5rem;
}

.card-title,
.card-text {
  word-wrap: break-word;
}

.btn-jokes {
  border: none;
  width: 100px;
  padding: 0.8rem 0;
  border-radius: 5px;
  font-size: 1.2rem;
  color: #fff;
  background-color: #dc3545;
}
</style>
