<template>
  <div class="main-menu">
    <nav>
      <li v-for="(link, index) in links" :key="index">
        <a :href="`${link.url}`">{{ link.name }}</a>
      </li>
    </nav>
  </div>
</template>

<script>
export default {
  name: 'MainMenu',
  props: {
    links: Array
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .main-menu {
    display: block;
    width: 100%;
    margin-bottom: 30px;
  }
  .main-menu nav {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: center;
    width: 100%;
    padding: 10px 0;
    background: #007bff;
    list-style: none;
  }
  .main-menu nav li {
    display: flex;
    flex-wrap: wrap;
    padding: 0 5px;
  }
  .main-menu nav li a {
    padding: 7px 15px;
    text-decoration: none;
    color: #FFFFFF;
    transition: 250ms ease-in-out 0s;
  }
  .main-menu nav li a.active,
  .main-menu nav li a:hover {
    color: #333;
  }
</style>
