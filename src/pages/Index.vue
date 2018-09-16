<template>
  <q-page class="flex flex-center">
         <div class="card shadow-" :class="classCard" @click="rotateCard()">
           <div class="card-content">
             <div class="q-pt-xl text-center img-front" :class="classCardFront" >
                <p class="text-weight-medium q-title text-grey-2">VIRTUAL CARD</p>
                <p class="text-weight-medium q-title text-grey-2">0000 0000 0000 0000</p>
                <p class="text-weight-medium q-mt-lg q-subheading text-grey-2">PATRICK PINHEIRO MONTEIRO</p>
            </div>
            <div class="img-back" :class="classCardBack" >
              <div class="retangulo q-mt-xl"></div>
              <div class="q-pt-sm q-ml-sm">
                <p class="text-weight-medium q-subheading text-grey-2">000</p>
              </div>
            </div>
           </div>
        </div>
  </q-page>
</template>

<script>
export default {
  name: 'PageIndex',
  data () {
    return {
      classCard: 'card-not-active',
      classCardBack: 'img-back-not-active',
      classCardFront: 'img-front-active',
      card: false
    }
  },
  methods: {
    rotateCard () {
      if (!this.card) {
        this.showCard()
        this.stateCard()
      } else {
        this.hideCard()
        this.stateCard()
      }
    },
    showCard () {
      this.classCard = 'card-active'
      setTimeout(() => {
        this.classCardBack = 'img-back-active'
        this.classCardFront = 'img-front-not-active'
      }, 400)
    },
    hideCard () {
      this.classCard = 'card-not-active'
      setTimeout(() => {
        this.classCardBack = 'img-back-not-active'
        this.classCardFront = 'img-front-active'
      }, 400)
    },
    stateCard () {
      this.card = !this.card
    }
  }
}
</script>

<style>
.card{
  height: 13em;
  width: 19em;
  border: solid 1px white;
  display: relative;
  margin-left: 5px;
  z-index: 3;
  border-radius: 1em;
  background:linear-gradient(to right, #002966 , #0066ff);
  text-shadow: 2px 2px #333333;
  cursor: pointer;
}

.card-active{
  transform: rotateY(180deg);
  transition-duration: 1.5s;
}

.card-not-active{
  transform: rotateY(0deg);
  transition-duration: 1.5s;
}

.card-content{
  /* border: solid 1px; */
  position: relative;
  /* margin: 0 auto; */
}

.retangulo {
  background: grey;
  height: 3em;
  width: 100%;
  display: relative;
}

.img-front-active {
  display: block;
  /* height: auto;
  transition: opacity 1s linear;
  opacity: 1;
  position: relative; */
}

.img-front-not-active {
  display: none;
  /* transition: opacity 1s linear;
  opacity: 0;
  height: 0;
  position: absolute; */
}

.img-back-active{
  display: block;
  transition-duration: 1.5s;
}

.img-back-not-active{
  display: none;
  transition-duration: 1.5s;
}

.img-front{
  transform: rotateY(0deg);
}
</style>
