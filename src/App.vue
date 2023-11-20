<template>
  <nav>
    <router-link to="/">Kalkulator karmy</router-link> 

  </nav>
  <router-view/>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: rgb(0, 168, 22);
}

#h1{
  color: rgb(0, 168, 22);

  
}
#caticon
{
  position: absolute;
  top:0;
  left:0;
}
.kalendarz{
  position: absolute;
  width:70px;
  margin-left: 31.75%;
}
h2{
  text-align: left;
  margin-left: 32%;
}
.ileDziennie{
  text-align: left;
  margin-left: 32%;
}
.ileWPuszce{
  text-align: left;
  margin-left: 32%;
}
#wybierzDate{
  text-align: left;
  margin-left: 35%;
  margin-top: 0.5%;
  color: red;
}
#potrzebaKupic{
  transform: scale(1.5);
}


</style>
