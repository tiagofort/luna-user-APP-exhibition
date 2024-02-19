<template>
  <div class="center mb-3">
    <v-app-bar app height="110px" elevation="0" color="white">
      <v-tabs centered>
        <ul class="menu-bar mb-5">
          <li>Home</li>
          <li>Acessories</li>
          <li>About us</li>
        </ul>
      </v-tabs>
    </v-app-bar>
  </div>
</template>


<style>
.center {
  text-align: center;
}

.menu-bar {
  border-radius: 25px;
  height: fit-content;
  display: inline-flex;
  background-color: rgba(251, 237, 228, 1);
  -webkit-backdrop-filter: blur(10px);
  backdrop-filter: blur(10px);
  align-items: center;
  padding: 0 10px;
  margin: 50px 0 0 0;
}
.menu-bar li {
  list-style: none;
  color: #b86935;
  font-family: sans-serif;
  font-weight: bold;
  padding: 12px 16px;
  margin: 0 8px;
  position: relative;
  cursor: pointer;
  white-space: nowrap;
}
.menu-bar li::before {
  content: " ";
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
  z-index: -1;
  transition: 0.2s;
  border-radius: 25px;
}
.menu-bar li:hover {
  /* color: white; */
  font-weight: bold;
}
.menu-bar li:hover::before {
  background: linear-gradient(to bottom, #fbede4, #fbede4);
  box-shadow: 0px 3px 20px 0px rgb(241, 186, 161);
  transform: scale(1.2);
}
</style>