<template>
  <div id="app">
    <nav
      id="nav"
      class="navbar is-primary"
      role="navigation"
      aria-label="main navigation"
    >
      <div class="navbar-brand">
        <a class="navbar-item" href="https://bulma.io">
          <img
            src="https://bulma.io/images/bulma-logo.png"
            width="112"
            height="28"
          />
        </a>
      </div>

      <div id="navbarBasicExample" class="navbar-menu">
        <div class="navbar-start">
          <div class="navbar-item">
            <div class="field">
              <p class="control has-icons-right">
                <input
                  class="input"
                  type="text"
                  placeholder="Pesquisa"
                >
                <span class="icon is-small is-right">
                  <i class="fas fa-search"></i>
                </span>
              </p>
            </div>
          </div>
        </div>

        <div class="navbar-end">
          <div class="navbar-item">
            <div class="buttons">
              <a class="button is-primary">
                <strong>Favoritos</strong>
              </a>
              <a class="button is-light"> Carrinho </a>
            </div>
          </div>
        </div>
      </div>
    </nav>
    <div class="columns is-mobile">
      <div class="column is-2 is-offset-1">
        <div v-for="(mov, index) in filmescolu1" :key="mov.id">
          <Filme
            :titulo_filme="mov.original_title"
            :num="index + 1"
            :id_filme="mov.id"
          />
        </div>
      </div>
      <div class="column is-2 is-offset-1">
        <div v-for="(mov, index) in filmescolu2" :key="mov.id">
          <Filme
            :titulo_filme="mov.original_title"
            :num="index + 1"
            :id_filme="mov.id"
          />
        </div>
      </div>
      <div class="column is-2 is-offset-1">
        <div v-for="(mov, index) in filmescolu3" :key="mov.id">
          <Filme
            :titulo_filme="mov.original_title"
            :num="index + 1"
            :id_filme="mov.id"
          />
        </div>
      </div>
      <div class="column is-2 is-offset-1">
        <div v-for="(mov, index) in filmescolu4" :key="mov.id">
          <Filme
            :titulo_filme="mov.original_title"
            :num="index + 1"
            :id_filme="mov.id"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Filme from "./components/Filme";
export default {
  name: "App",
  data() {
    return {
      filmes: [],
      filmescolu1: [],
      filmescolu2: [],
      filmescolu3: [],
      filmescolu4: [],
    };
  },
  created: function () {
    axios
      .get(
        "https://api.themoviedb.org/3/list/50941077760ee35e1500000c?api_key=b02c26e7cdf8332f6747485120b222dc&language=pt-BR"
      )
      .then((res) => {
        //console.log(res.data.items);
        this.filmes = res.data.items;
        this.filmescolu1 = this.filmes.splice(0, 6);
        this.filmescolu2 = this.filmes.splice(6, 6);
        this.filmescolu3 = this.filmes.splice(12, 6);
        this.filmescolu4 = this.filmes.splice(18, 6);
        console.log(res);
      });
  },
  components: {
    Filme,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#nav {
  margin-bottom: 1.5rem;
}
</style>
