<template>
  <div class="card"></div>
</template>

<script>
export default {

}
</script>

<style scoped>
.card{
  width: 200px;
  height: 232px;
  border-radius: 5px;                                         /* ovallestirme icin */
  border: 1px solid #666;
  margin-left: 15px;
  background-image: url("../assets/vue-js-egitim-background.jpg");
  background-size: cover;                     /*  Icini kapla  */
  background-repeat: no-repeat;
  background-position: center;               /*Hizalamaya ortadan basla */
  box-shadow: 0px 9px 55px #666;
}
.card:first-child{
  margin-left: 0px;
}
.card img{
  width: 100%;
  height: 100%;
}
</style>