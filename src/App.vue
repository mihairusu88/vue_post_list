<template>
  <div id="app">
    <div class="loader" v-if="this.loading">
      <div class="loading-animation"></div>
    </div>
    <div class="main" v-if="!this.loading">
      <MainMenu :links="menuLinks" />
      <div class="container">
        <div class="post-list">
          <PostItem v-for="(post, index) in posts" :key="index" :post="post" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import MainMenu from './components/common/main-menu.vue';
import PostItem from './components/post-item.vue';

export default {
  name: 'app',
  components: {
    MainMenu,
    PostItem
  },
  created: function(){
    this.loading = true;
    console.log('here', this.loading);
  },
  mounted: async function(){
    this.loading = false;
    this.menuLinks = [
      {
        url: '#',
        name: 'Home'
      },
      {
        url: '#',
        name: 'My Profile'
      }
    ];

    try {
      const posts = await fetch('https://jsonplaceholder.typicode.com/posts')
                            .then(res => res.json())
                            .then(data => data);
      this.posts = posts;
    } catch (err){
      console.log('Oops, we have an error!', err);
    }
  },
  data: function(){
    const dataValues = {
      loading: this.loading,
      posts: this.posts,
      menuLinks: this.menuLinks
    }

    return dataValues;
  }
}
</script>

<style>
* {
  margin: 0;
  box-sizing: border-box;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
}

.btn {
  padding: 7px 15px;
  line-height: 1.6;
  text-transform: uppercase;
  text-decoration: none;
  font-size: 12px;
  border-radius: 7px;
}
.btn-primary {
  color: #FFFFFF;
  background: #007bff;
  transition: 250ms ease-in-out 0s;
}
.btn-primary:hover {
  opacity: 0.6;
}

.post-list {
  display: flex;
  flex-wrap: wrap;
}

#app {
  font-family: 'Arial', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

/*=== Loading Animation === */
.loader {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: center;
  position: fixed;
  z-index: 10000;
  background: #FFFFFF;
  width: 100%;
  height: 100%;
}
.loader .loading-animation {
    border-width: 3px;
    border-style: solid;
    border-color: #dddddd #dddddd #007bff #007bff;
    height: 45px;
    width: 45px;
    border-radius: 100%;
    animation: spin 1.1s infinite linear;
}

@keyframes "spin" {
    from {
        -webkit-transform: rotate(0deg);
        -moz-transform: rotate(0deg);
        -o-transform: rotate(0deg);
        -ms-transform: rotate(0deg);
        transform: rotate(0deg);
    }
    to {
        -webkit-transform: rotate(359deg);
        -moz-transform: rotate(359deg);
        -o-transform: rotate(359deg);
        -ms-transform: rotate(359deg);
        transform: rotate(359deg);
    }
}

@-moz-keyframes "spin" {
    from {
        -moz-transform: rotate(0deg);
        transform: rotate(0deg);
    }
    to {
        -moz-transform: rotate(359deg);
        transform: rotate(359deg);
    }
}

@-webkit-keyframes "spin" {
    from {
        -webkit-transform: rotate(0deg);
        transform: rotate(0deg);
    }
    to {
        -webkit-transform: rotate(359deg);
        transform: rotate(359deg);
    }
}

@-ms-keyframes "spin" {
    from {
        -ms-transform: rotate(0deg);
        transform: rotate(0deg);
    }
    to {
        -ms-transform: rotate(359deg);
        transform: rotate(359deg);
    }
}

@-o-keyframes "spin" {
    from {
        -o-transform: rotate(0deg);
        transform: rotate(0deg);
    }
    to {
        -o-transform: rotate(359deg);
        transform: rotate(359deg);
    }
}
/*=== END Loading Animation === */
</style>
