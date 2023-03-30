<script>
import years from './assets/data/years_parteistaerke_1919-2019.json'

export default {
  data() {
    return {
      years: years
    }
  }
}
</script>


<template>
  <div class="intro">
    <h1 class="title__left">Parteistärke 1919 - 2019</h1>
    <p class="text">
      Visualisierungen der Parteistärken von 1919 bis 2019.
    </p>
  </div>
  <div class="wrapper" v-for="year in years" :key="year">
    <h2>{{ year.Year }}</h2>
    <div class="content__wrapper">
      <div class="container" v-for="party in year.parties" :key="party">
        <div class="bar" :style="{height: party.Wahlanteil * 3.2 + '%', backgroundColor: party.Colour }">
      </div>
      <div class="label">
          <p class="partei">{{ party.Partei }}</p>
          <p>{{ party.Wahlanteil }}%</p>
        </div>
      </div>
    </div>  
  </div>
  <h1 class="title">Übersicht</h1>
  <div class="wrapper__grid">
    <div v-for="year in years" :key="year">
      <h2 class="year__grid">{{ year.Year }}</h2>
      <div class="content__wrapper__grid">
        <div class="container__grid" v-for="party in year.parties" :key="party">
          <div class="bar" :style="{height: party.Wahlanteil * 3.2 + '%', backgroundColor: party.Colour }">
        </div>
        </div>
      </div> 
    </div>
  </div> 

</template>

<style scoped>

.intro {
  display: flex;
  flex-flow: column wrap;
  height: 50vh;
  width: 100vw;
}
.text {
  font-size: 24px;
  margin-left: 0px;
}
  .wrapper {
    display: flex;
    margin: 0 auto;
    justify-content: center;
    flex-flow: row nowrap;
    margin-bottom: 50px;
  }

  .content__wrapper {
    display: flex;
    margin: 0 auto;
    justify-content: center;
    flex-flow: row nowrap;
    margin-bottom: 50px;
    height: 100vh;
    width: 85vw;
  }

  .container {
    display: flex;
    flex-flow: row wrap;
    justify-content: center;
    align-items: flex-end;
    height: 100vh;
    width: 10%;
    border-right: thin solid #f1f1f1;
    background-color: white;
  }

  .container:hover {
    filter: drop-shadow(0 0 0.75rem grey);
  }

  .bar {
    width: 100%;
  }

  .title {
    margin-top: 150px;
    margin-bottom: 150px;
  }

  .partei {
    font-weight: bold;
  }

  .label {
    display: flex;
    flex-flow: column wrap;
    justify-content: center;
    align-items: center;
  }

  .wrapper__grid {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr;
    grid-template-rows: 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr;
    gap: 10px;
    justify-content: center;
    flex-flow: row nowrap;
    margin-bottom: 50px;
  }

  .content__wrapper__grid {
    display: flex;
    margin: 0 auto;
    justify-content: center;
    flex-flow: row nowrap;
    margin-bottom: 50px;
    height: 10vh;
    width: 10vw;
  }

  .container__grid {
    display: flex;
    flex-flow: row nowrap;
    align-items: flex-end;
    height: 10vh;
    width: 10vw;
  }
</style>
