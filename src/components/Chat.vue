<template>
    <div class="chat__block">
            <div class="chat__block-nav">
                <img class="chat__block-ava" src="../assets/img/putin.jpg" alt="">
                <p class="chat__block-name">
                    Володимиир Путин
                    <span>в сети</span>
                </p>
            </div>
        <div class="chat__block-box">
          <div class="chat__block-messages">
            <div class="chat__block-container">
                <div class="chat__block-your message">
                  <p class="chat__block-text">{{ }}</p>
                  <span></span>
              </div>
            </div>
            <div class="chat__block-container">
              <div class="chat__block-my message">
                <span></span>
                <p class="chat__block-text">{{  }}</p>
              </div>
              </div>
          </div>
        </div>         
          <div class="chat__block-bottom">
            <textarea class="chat__block-input" placeholder="Написать сообщение..."></textarea>
            <a href="#!" class="chat__block-photo"><img src="../assets/img/svg/photo.svg" alt=""></a>
          </div>
    </div>
</template>

<script>




export default {
  components:{
  },
  data(){
    return{

    }
  },
  props:{
    bool:Boolean,
    arr:Array
  },
  methods:{
  }
}
</script>

<style>

</style>