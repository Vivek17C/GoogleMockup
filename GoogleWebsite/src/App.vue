<template>
  <div v-bind:class="{ dark: theme === 'dark' }">
    <!-- Top bar -->
    <header class="topbar">
      <div>
        <a href="#">About</a>
        <a href="#">Store</a>
      </div>
      <div>
        <a href="#">Gmail</a>
        <a href="#">Images</a>
        <a href="#">Sign in</a>
      </div>
    </header>

    <!-- Main -->
    <main>
      <h1 class="logo">
        <span class="blue">G</span><span class="red">o</span><span class="yellow">o</span><span class="blue">g</span><span class="green">l</span><span class="red">e</span>
      </h1>

      <div class="search">
        <input v-model="query" type="text" />
      </div>

      <div class="buttons">
        <button v-on:click="noop">Google Search</button>
        <button v-on:click="noop">I'm Feeling Lucky</button>
      </div>
    </main>

    <!-- Foooter -->
    <footer>
      <div class="left">
        <a href="#">Advertising</a>
        <a href="#">Business</a>
        <a href="#">How Search Works</a>
      </div>
      <div class="right">
        <a href="#">Privacy</a>
        <a href="#">Terms</a>
        <button v-on:click="toggleTheme">Settings</button>
      </div>
    </footer>
  </div>
</template>

<script>
export default {
  data() {
    return {
      query: '',
      theme: localStorage.getItem('theme') ? localStorage.getItem('theme') : 'light'
    }
  },
  mounted() {
    if (this.theme === 'dark') {
      document.body.classList.add('dark')
    } else {
      document.body.classList.remove('dark')
    }
  },
  methods: {
    toggleTheme() {
      if (this.theme === 'light') {
        this.theme = 'dark'
        localStorage.setItem('theme', 'dark')
        document.body.classList.add('dark')
      } else {
        this.theme = 'light'
        localStorage.setItem('theme', 'light')
        document.body.classList.remove('dark')
      }
    },
    noop() {
      
    }
  }
}
</script>

<style>
body {
  margin: 0;
  font-family: Arial, sans-serif;
}

/* Top bar */
.topbar {
  display: flex;
  justify-content: space-between;
  padding: 10px 20px;
}
.topbar a {
  margin: 0 10px;
  text-decoration: none;
  color: black;
}
.topbar a:hover {
  text-decoration: underline;
}

/*Logo*/
.logo {
  font-size: 80px;
  text-align: center;
  margin-top: 100px;
}
.blue { color: #4285f4; }
.red { color: #ea4335; }
.yellow { color: #fbbc05; }
.green { color: #34a853; }

/* Search */
.search {
  text-align: center;
  margin: 20px;
}
.search input {
  width: 350px;
  padding: 8px;
  font-size: 16px;
}

/* Buttons */
.buttons {
  text-align: center;
  margin-top: 20px;
}
.buttons button {
  margin: 0 5px;
  padding: 8px 16px;
}

/* Footer */
footer {
  display: flex;
  justify-content: space-between;
  padding: 10px 20px;
  position: fixed;
  bottom: 0;
  width: 100%;
  background: pink; 
}
footer a,
footer button {
  margin: 0 5px;
  text-decoration: none;
  color: black;
  background: none;
  border: none;
  cursor: pointer;
  font: inherit;   
  padding: 0;      
}
footer a:hover,
footer button:hover {
  text-decoration: underline;
}

/* Dark mode */
.dark {
  background: #202124;
  color: white;
}
.dark a,
.dark button {
  color: white;
}
.dark footer {
  background: #303134; /* dark mode foooter */
}
</style>
