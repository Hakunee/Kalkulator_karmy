<template>
  <div class="home">
    <img id= "caticon" alt="Cat icon" src="../assets/cat-icon.png" width="150">

    <H1 id="h1">Kalkulator</H1>
    <H2>Skrypt ten ma na celu przeliczenie ile puszek karmy należy zamówić dla koteła</H2>
    <div class="ileDziennie">
      <b>Podaj dzienne spożycie wojego koteła(g)</b>
      <input  v-model.number="ileDziennieAmmount" type="number" >
       <span v-if="ileDziennieAmmount">{{ ileDziennieAmmount }}<b>g</b></span>
    </div>
    <div class="ileWPuszce">
      <b>Podaj pojemność puszki karmy (g)</b>
      <input v-model="ileWPuszce" type="text">
      <span v-if="ileWPuszce">{{ ileWPuszce }}g</span>
    </div> 
    <div class="kalendarz">
    
    <Datepicker v-model="date" model-type="yyyy-MM-dd" teleport-center/>
    </div>
    <div id="wybierzDate" v-if="!date">Wybierz datę!</div>
    <div v-show="false" >
      <b>Wybrana data: </b>{{ date }} 
    </div>
    <div v-show="false" ><b>Dzisiejsza data:</b> {{ currentDate() }} 
    </div>
    <div v-if="date"  v-show="false" >Różnica w dniach: {{ calculateDateDifference() }}
    </div>
    <div v-show="false" ><b>Pucha starczy na: </b>{{ amountOfFood() }}
    </div>
    <div id="potrzebaKupic"><b>Potrzeba kupić {{ ileTrzeba() }}</b></div>
  </div>


</template>


<script>
  import Datepicker from '@vuepic/vue-datepicker';
  import '@vuepic/vue-datepicker/dist/main.css';
  
  // const date = ref(new Date);
  // var t= new Date();

  



export default {
  name: 'HomeView',
  components: { Datepicker},
  data(){
    return {
      ileDziennieAmmount:'',
      ileWPuszce:'',
      date:'',
      doNMsc:'',
      sliced:'',
      datePoStringu:'',
      dayDifference:0,
      naIleStarczyPucha: 0,
      trzebaKupic:'',
    }
  },
  methods:{
    currentDate() {
      const current = new Date();
      const formattedCurrentDate = `${current.getFullYear()}-${current.getMonth() + 1}-${current.getDate()}`;
      return formattedCurrentDate;
    },
    calculateDateDifference() {
      
      const selectedDate = new Date(this.date);
      const currentDate = new Date();
      const timeDifference = selectedDate.getTime() - currentDate.getTime();
      this.dayDifference = timeDifference / (1000 * 3600 * 24);
      return Math.floor(this.dayDifference); 
    },
    amountOfFood() {
      this.naIleStarczyPucha = this.ileWPuszce / this.ileDziennieAmmount;
      console.log(this.naIleStarczyPucha)
      return this.naIleStarczyPucha;
      // var trzebaKupic = this.dayDifference / this.naIleStarczyPucha;
      // console.log(trzebaKupic)
      // return Math.ceil(trzebaKupic);
    },
    ileTrzeba(){

      this.trzebaKupic = this.dayDifference / this.naIleStarczyPucha;
      return Math.ceil(this.trzebaKupic);
    },
  },
}

</script>
<style>
#app
{
  background-color:rgb(212, 209, 209) ;
  background:rgb(212, 209, 209) ;
}

</style>