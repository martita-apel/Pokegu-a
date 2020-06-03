<template>
  <div>
    <h1>{{ msg }}</h1>
    <form @submit.prevent="search">
      <input v-model="pokemon.name" type="text" placeholder="Nombre" />
      <button @click="search" type="submit">
        <i class="fas fa-search"></i>
      </button>
    </form>

    <div class="card">
      <img :src="imgPokemon" alt="" />
      <div class="cuerpo">
        <h3 class="titulo">{{ pokemon.name.toUpperCase() }}</h3>
        <hr />
        <h4>Movimientos:</h4>
        <ul>
          <p class="movi" v-for="move in movPokemon" :key="move">
            {{ move.move.name }} /
          </p>
        </ul>
        <h4>Habilidades:</h4>
        <ul>
          <p class="habi" v-for="abilitie in abPokemon" :key="abilitie">
            {{ abilitie.ability.name }} /
          </p>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Pokedex",
  props: {
    msg: String,
  },
  data() {
    return {
      pokemon: {
        name: "pikachu",
        sprites: "",
        moves: [],
        abilities: "",
      },
    };
  },
  methods: {
    search() {
      fetch(`https://pokeapi.co/api/v2/pokemon/${this.pokemon.name}`)
        .then((response) => response.json())
        .then((response) => (this.pokemon = response));
    },
    /*  nombrePokemon() {
      if (this.pokemon.name.value != "") {
        return this.pokemon.name.toUpperCase();
      } else {
        return (this.pokemon.name.value = "pikachu");
      }
    }, */
  },
  created() {
    /* window.addEventListener("input", () => {
      return (this.pokemon.name.value = "pikachu");
    }); */
    this.search();
  },
  computed: {
    imgPokemon() {
      return this.pokemon.sprites.front_default;
    },
    movPokemon() {
      return this.pokemon.moves;
    },
    abPokemon() {
      return this.pokemon.abilities;
    },
    /* valInput(value) => {
      if (value == "") {
        alert("Debes ingresar tu correo");
      } else if (value.length > 100) {
        alert("Tu correo no es válido");
      }
    } */
  },
};
</script>

<style scoped>
h1 {
  font-family: "VT323", monospace;
  font-size: 50px;
  padding: 0;
  margin-top: 0;
}
form {
  display: inline-flex;
  margin: auto;
  margin-bottom: 50px;
}
input {
  font-size: 30px;
  font-weight: lighter;
  padding: 20px 15px;
  border: 0;
  border-radius: 10px;
}

button {
  background-color: #d11000;
  margin-left: 10px;
  padding: 10px 10px 5px 12px;
  color: white;
  border: 0;
  border-radius: 10px;
}

button:hover {
  color: gainsboro;
}

i {
  font-size: 40px;
  padding: 10px 5px;
}

.card {
  width: 60%;
  margin: auto;
  background-color: white;
  border-radius: 15px;
}
hr {
  margin: 0 20px;
}
ul {
  margin: 20px;
  margin-top: 0;
  padding: 0;
}
h4 {
  margin-bottom: 0;
}
.movi {
  display: inline-flex;
  margin: 0;
}
.habi {
  margin: 0;
  padding-bottom: 50px;
  display: inline-flex;
}
</style>
