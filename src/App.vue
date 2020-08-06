<template>
  <component
    :is = "activeComponent"
  >

  </component>
</template>
<script>

import GameCards from "./components/GameCards";
import Failure from "./components/Failure";
import Celebrate from "./components/Celebrate";


export default {
  data(){
    return{
      activeComponent: "app-game-card"
    }
  },
  components: {
    appGameCard: GameCards,
    appCelebrate: Celebrate,
    appFailure: Failure
  }


}
</script>
<style></style>
