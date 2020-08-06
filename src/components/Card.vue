<template>
  <div class = "card">
    <img src = "../assets/card-1.jpg" alt="">
  </div>
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
  background-color: purple;
  margin-left: 15px;
}
.card:hover{
  box-shadow: 0px 5px 48px #666;
  transition: box-shadow .5s;            /* vermis oldugumuz ozelligi vermis oldugumuz sureye yayarak gerceklestirir*/
}
.card img{
  width: 100%;
  height: 100%;
}
</style>