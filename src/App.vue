<script>
import Nav from './components/Nav.vue'

export default {
  components: { Nav },
  data() {
    return {
      pets: [
        {id: 1, name: "Buddy", type: "Dog", age: 2, adopted: true},
        {id: 2, name: "Mittens", type: "Cat", age: 4, adopted: false},
        {id: 3, name: "Tweety", type: "Bird", age: 1, adopted: true},
        {id: 4, name: "Shadow", type: "Dog", age: 5, adopted: false},
      ],
      searchResult: ''
    }
  },
  methods: {
    handleSearch(name) {
      const pet = this.pets.find(pet => pet.name.toLowerCase() === name.toLowerCase())
      if (pet) {
        this.searchResult = `${pet.name} is ${pet.adopted ? "adopted" : "available"}`
      }
      else {
        this.searchResult = `No pet found by the name ${name}.`
      }
    }
  }
}

</script>

<template>
  <div>
    <Nav @search-pet="handleSearch" />
    <p>{{ searchResult }}</p>
    <router-view :pets="pets" />
  </div>
 
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
