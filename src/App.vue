<template>
  <div id="app">
        <!-- navbar -->
        <nav v-if="this.$route.name !== 'Login' && this.$route.name !== 'Signup' " class="navbar navbar-expand-lg navbar-light bg-light border " >
              <router-link to="/">
                  <img src="/Images/logo.png" id="navbarImgLogo"/>
              </router-link> 
          
              <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
              </button>

              <div class="collapse navbar-collapse" id="navbarSupportedContent">
                  <ul class="navbar-nav mr-auto">
                    <li class="nav-item active">
                      <router-link to="/" class="nav-link" > Arhiva <span class="sr-only">(current)</span></router-link>  <!-- current?-->
                    </li>
                    <li class="nav-item active"> 
                        <router-link to="/scan" class="nav-link"> Skeniraj <span class="sr-only">(current)</span></router-link>    
                    </li>

                    <li class="nav-item active">
                        <router-link to="/manualscan" class="nav-link"> Ručno dodavanje <span class="sr-only">(current)</span></router-link>    
                    </li>
                  </ul>
                  <router-link to="/alias_list">
                    <button class="btn btn-primary my-2 my-sm-0" type="button" style="border-radius: 5px; margin: 0 5px 0 5px; padding:0 2px 0 2px;">
                      <i class="fa fa-address-card fa-2x" aria-hidden="true"></i>
                    </button> 
                  </router-link>
                  
                  <button v-on:click = "logout()" class="btn btn-primary my-2 my-sm-0" type="button" style="border-radius: 5px;">Odjavi se</button> 
              </div>
          </nav>
    <router-view/>
  </div>
</template>

<script>
import store from '@/store.js';
import { Auth } from "@/services";

export default {
  data(){
    return {
      ...store,
      auth: Auth.state
    }
  },

  methods : {
    logout() {
        Auth.logout();
        this.$router.go();
    },
  },

  mounted(){
  }
}
</script>

<style lang="scss">

// popraviti : povezati putanje route u index.js , hover i active na izbore menija, backend logotipa, navbar fiksan?

#app {
  font-family:  'Montserrat', Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  
}

@font-face {font-family: "BillabongW00-Regular"; src: 
url("//db.onlinewebfonts.com/t/6d32b8e06f40fb7698cfb714b9e7975d.eot"); 
src: url("//db.onlinewebfonts.com/t/6d32b8e06f40fb7698cfb714b9e7975d.eot?#iefix") 
format("embedded-opentype"), url("//db.onlinewebfonts.com/t/6d32b8e06f40fb7698cfb714b9e7975d.woff2") 
format("woff2"), url("//db.onlinewebfonts.com/t/6d32b8e06f40fb7698cfb714b9e7975d.woff") 
format("woff"), url("//db.onlinewebfonts.com/t/6d32b8e06f40fb7698cfb714b9e7975d.ttf") 
format("truetype"), url("//db.onlinewebfonts.com/t/6d32b8e06f40fb7698cfb714b9e7975d.svg#BillabongW00-Regular") 
format("svg"); }


#navbarImgLogo{
  font-family: "BillabongW00-Regular";
}

.navbar-brand{
  font-size:50px;
  letter-spacing: 0;
  opacity: 1;
}

.logo-brand{
  margin: -10px 20px -30px 0px;
}

.nav-item {
  padding-right: 10px;
  padding-left: 10px;
  font-size: 20px;
}

.border {
  border: 2px solid #00a2ff !important;
}

.navbar-light {
    background-color: white !important;
    padding:0px;
}

/*
router-link:hover{
   color: #00FF00; 
} 
*/

</style>
