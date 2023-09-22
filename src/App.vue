<script>
export default {
  data() {
    return {
      city: ""// переменые
    }
  }
}
</script>

<template>  
  <div class="wrapper">
    <h1>Погодное приложение</h1>
    <p>Узнать погоду в {{ city }}</p>
    <input type="text" v-model="city" name="" id="" placeholder="Введите город">
    <button>Получить погоду</button>
  </div>
</template>

<style scoped>
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
</style>
