<template>
  <div class = "game-area">
    <h1 class = "title">Mü <span>Nerede</span><strong>?</strong></h1>
    <h4 class = "description">Açık kartlardan birini seçtikten sonra, kapalı olan karta tıklayınız</h4>
    <div class = "container">
     <transition-group name = "rotate-all" class = "container" appear>
       <app-card
           :key = "card.id"
           :class = "{'shadow': selectedCard === card.id}"
           @click.native = "selectedCard = card.id"
           v-for = "card in cards"
           :card = "card">
       </app-card>
     </transition-group>
    </div>
    <div class="container">
      <transition name="rotate" mode="out-in">
        <component
            @click.native="showCard(answer)"
            :card = "answer"
            :is = "activeCard">
        </component>
      </transition>
    </div>
  </div>
</template>

<script>
import Card from "./Card"
import DefaultCard from "./DefaultCard";

export default {
  data(){
    return{
      selectedCard: null,
      answer: {},
      activeCard: "app-default-card",
      cards: [
        {id:1, component: "app-card", image: "/src/assets/card-1.jpg"},
        {id:2, component: "app-card", image: "/src/assets/card-2.jpg"},
        {id:3, component: "app-card", image: "/src/assets/card-3.jpg"},
        {id:4, component: "app-card", image: "/src/assets/card-4.jpg"},
        {id:5, component: "app-card", image: "/src/assets/card-5.jpg"}
      ]
    }
  },
  components: {
    appCard: Card,
    appDefaultCard: DefaultCard
  },
  created() {
    let answer = Math.ceil(Math.random()* this.cards.length);
    this.answer = this.cards[answer-1];
    console.log(this.answer);
  },
  methods: {
    showCard(answer){
      if(this.selectedCard == null){
        alert("İlk olarak bir kart seçiniz");
      }else{
        this.activeCard = answer.component;
        setTimeout(() => {
          if(answer.id === this.selectedCard){
            alert("Doğru");
            this.$emit("activeComponentEvent", "app-celebrate");
          }else{
            alert("Yanlış");
            this.$emit("activeComponentEvent", "app-failure");
          }
        },1000)
      }
    }
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
  .shadow{
    box-shadow: 0px 5px 48px #30969f !important ;
    transition: box-shadow .5s;
  }


  /********************Acik  kart animasyonlari icin gerekli olan transition tanımlari**********************/


  .rotate-all-enter{}
  .rotate-all-enter-active{
    animation: rotate-all ease-in-out 2s forwards;           /*yavas basla ortada hizlan yavas bit*/
  }
  .rotate-all-leave{}
  .rotate-all-leave-active{}
  
  @keyframes rotate-all {
    from{
      transform: rotateY(0);
    }
    to{
      transform: rotateY(1440deg);
    }
  }

  /********************Kapali  kart animasyonlari icin gerekli olan transition tanımlari**********************/

  .rotate-enter{}
  .rotate-enter-active{
    animation: rotate-in  ease-in-out .5s forwards;           /*yavas basla ortada hizlan yavas bit*/
  }
  .rotate-leave{}
  .rotate-leave-active{
    animation: rotate-out  ease-in-out .5s forwards;
  }

  @keyframes rotate-in {
    from{
      transform: rotateY(90deg);
    }
    to{
      transform: rotateY(0deg);
    }
  }

  @keyframes rotate-out {
    from{
      transform: rotateY(0deg);
    }
    to{
      transform: rotateY(90deg);
    }
  }

</style>