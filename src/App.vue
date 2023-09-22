<script>
import axios from 'axios'

export default {
  data() {
    return {
      city: "",// переменые
      error: "",
      info: null,
    }
  },
  computed: {
    cityName() {
      return '"' + this.city + '"'
    }
  },
  methods: {
    getWeatcher() {
      if (this.city.trim().length < 2) {
        this.error = "Нужно название больше одного символа"
        return false
      }
      this.error = ''

      axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&appid=03c1766a65006cabfc6b7cb74eeb443e`)
        .then(res => this.info = res)
    }

  }
}
</script>

<template>  
  <div class="wrapper">
    <h1>Погодное приложение</h1>
    <p>Узнать погоду в {{ city == "" ? "вашем городе" : cityName }}</p>
    <input type="text" v-model="city" name="" id="" placeholder="Введите город">
    <button v-if="city != ''" @click="getWeatcher()">Получить погоду</button>
    <button disabled v-else>Введите название города</button>
    <p class="error" v-show="error != ''">{{ error }}</p>

    <p v-show="info != null">{{ info }}</p>
  </div>
</template>

<style scoped>
.error {
  color: red;
}
.wrapper {
  width: 900px;
  height: 500px;
  border-radius: 50px;
  padding: 50px 20px 20px;
  background-color: #1f0f24;  
  text-align: center;
  color: #fff;
}
.wrapper h1 {
  margin-bottom: 20px;
}

.wrapper input {
  margin-top: 30px;
  background:transparent;
  border: 0;
  border-bottom: 2px solid #110813;  
  font-size: 14px;
  padding: 5px 8px;
  outline: none;
  color:#fff;
}
.wrapper input:focus{
  border-bottom-color: #6e2d7d;
}

.wrapper button {
  background-color:#e3bc4b;
  color: #fff;
  border-radius: 10px;
  border: 2px solid #b99935;
  padding: 10px 15px;
  margin-left: 20px;
  cursor: pointer;
  transition: transform .5s ease;
}
.wrapper button:hover {
  transform: scale(1.1) translateY(-5px);
}
.wrapper button:disabled {
  background-color: #746027;
  cursor: not-allowed;
}
</style>
