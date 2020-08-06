<template>
  <div class = "game-area">
    <h1 class = "title">Mü <span>Nerede</span><strong>?</strong></h1>
    <h4 class = "description">Açık kartlardan birini seçtikten sonra, kapalı olan karta tıklayınız</h4>
    <div class = "container">
    </div>
    <div class="container">
      <app-card v-for="i in 5"></app-card>
    </div>
  </div>
</template>

<script>
import Card from "./Card"

export default {
  components:{
    appCard: Card
  }
}
</script>

<style scoped>
  .title{
    text-align: center;
    color: rosybrown;
  }
  .title span{
    color: mediumpurple;
  }
  .title strong{
    color: darkred;
  }
  .container{
    display: flex;            /*Yanyana hizaladi*/
    justify-content: center;           /*Yatay olarak ortala*/
    align-items: center;            /*dikey ortala*/
    margin-top: 50px;
  }
  .description{
    color: gray;
    text-align: center;
  }

</style>