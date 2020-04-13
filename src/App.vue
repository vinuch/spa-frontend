<template>
  <div id="app">
    <Banner />
    <div class="banner">
      <div class="banner__img">
        <img src="./assets/covid.jpg" sizes="(max-width: 600px) 480px,
            800px" alt="covid">
      </div>
      <div class="banner__text">
        <h1>Welcome to the COVID-19 response web app</h1>
        <p>
          The assessment empowers me to attempt helping society and leaders prepare for the real
          big problem of COVID-19, which is its impact on lives, health systems, supply chains,
          and the economy
          Get an estimate of COVID-19 related activity in your current location
        </p>
        <h4>
          Kindly fill out the form below to get estimated
          data on the corona virus for a particular region
        </h4>

    <form action="">
      <h4>Region details</h4>
      <div>
        <label for="region-name">Region Name<br>
        <input type="text" name="region-name" data="data-population" placeholder="Region Name"
        v-model="input.region.name"
        required>
        </label>
      </div>
      <div>
        <label for="regionAvgAge">Region Average Age<br>
        <input type="text" name="regionAvgAge" data="data-population"
        placeholder="Region Average Age"
        v-model="input.region.avgAge"
        required>
        </label>
      </div>
      <div>
        <label for="regionAvgIncome">Region Average Daily Income (USD)<br>
        <input type="text" name="regionAvgIncome" data="data-population"
        placeholder="Region Average Daily Income (USD)"
        v-model="input.region.avgDailyIncomeInUSD"
        required>
        </label>
      </div>
      <div>
        <label for="regionAvgIncomePopulation">Region Average Income Population<br>
        <input type="text" name="regionAvgIncomePopulation" data="data-population"
        placeholder="Region Average Income population"
        v-model="input.region.avgDailyIncomeInPopulation"
        required>
        </label>
      </div>
      <h4>Other Information</h4>
      <div>
        <label for="periodType">Period Type<br>
        <select name="periodType" data="data-period-type" v-model="input.periodType" required>
          <option value="Months">Months</option>
          <option value="Weeks">Weeks</option>
          <option value="Days">Days</option>
        </select>
        </label>
      </div>
      <div>
        <label for="poulation">Time to ELapse<br>
        <input type="number" name="timeToElapse" data="data-time-to-elapse"
        placeholder="Time to elapse "
        v-model="input.timeToElapse"
        required>
        </label>
      </div>
      <div>
        <label for="reportedCases">Reported Cases<br>
        <input type="number" name="reportedCases" data="data-reported-cases"
        placeholder="Reported Cases"
        v-model="input.reportedCases"
        required>
        </label>
      </div>
      <div>
        <label for="poulation">Population<br>
        <input type="number" name="population" data="data-population" placeholder="Population"
        v-model="input.population"
        required>
        </label>
      </div>
      <div>
        <label for="totalHospitalBeds">Total hospital beds<br>
        <input type="number" name="totalHospitalBeds" data="data-total-hospital-beds"
        placeholder="Total hospital beds"
        v-model="input.totalHospitalBeds"
        required>
        </label>
      </div>
      <button data="data-go-estimate" class="btn-submit" @click.prevent="estimate">
        Get Estimate</button>
    </form>
    <div v-if="result">
      <p v-for="(value, index) in result" :key="index">{{ value }}</p>
    </div>
      </div>
    </div>
  </div>
</template>

<script>
import Banner from './components/Banner.vue';
// import covid19ImpactEstimator from '../../src/estimator';

export default {
  name: 'App',
  components: {
    Banner,
  },
  data() {
    return {
      input: {
        region: {
          name: '',
          avgAge: 0,
          avgDailyIncomeInUSD: 0,
          avgDailyIncomeInPopulation: 0,
        },
        periodType: '',
        timeToElapse: 5,
        reportedCases: 0,
        population: 0,
        totalHospitalBeds: 0,
      },
      result: '',
    };
  },
  methods: {
    // estimate() {
      
    //   // this.result = covid19ImpactEstimator(this.input);
    //   // console.log(Object.values(this.result));
    // },
  },
};
</script>

<style>
body {
  background: #008ed1;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #0a0505;
  margin-top: 60px;
}
.banner {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}
.banner__text {
  flex-basis: 100%;
}
.banner__img {
  flex-basis: 100%;
}
.banner__img img{
  width: 25rem;
}
input, select {
  width: 80%;
  margin: .5rem 0;
  padding: .3rem;
}
.btn-submit {
  padding: .4rem;
  background-color: #feae6d;
  border: none;
}
.btn-submit:hover {
  transform: translateY(-2px);
}

@media screen and (min-width: 480px){
  .banner__text {
    flex-basis: 40%;
  }
  .banner__img {
    flex-basis: 40%;
  }
  .banner__img img{
    width: 35rem;
  }
  
}
</style>
