<template>
  <div class="chat">
    <div class="chat__block " v-for="el in users" :key='el.id'>
        <div class="chat__block-nav">
            <img class="chat__block-ava" :src="require(`../assets/img/${el.img}`)" alt="">
            <p class="chat__block-name">
                {{el.name}}
                {{getStatus(el.id,el.msge)}}
                <span>{{ el.status }}</span>
              </p>
            </div>
        <div class="chat__block-box">
          <div class="chat__block-messages">
            <div class="box-message" v-for="(mesges,id) in arr" :key="id">
              <div class="chat__block-container"  v-if="mesges.id == el.id">
                <div :class="styleOne">
                  <span>{{mesges.date}}</span>
                  <div class="chat__block-text" v-if="!mesges.img">{{ mesges.message}}</div>
                  <div class="chat__block-text" v-else><img :src="mesges.img" alt="">{{ mesges.message}}
                    <span>{{mesges.date}}</span>
                  </div>
                </div>
              </div>
            <div class="chat__block-container" v-else>
              <div :class="styleTwo">
                  <div class="chat__block-text" v-if="!mesges.img">
                    {{ mesges.message}}
                  </div>
                  <div class="chat__block-text" v-else>
                    <img :src="mesges.img" alt="">
                    {{ mesges.message}}
                    </div>
                <span>{{mesges.date}}</span>
              </div>
          </div>
          </div>
        </div>
        </div>         
          <div class="chat__block-bottom">
            <textarea class="chat__block-input" placeholder="Написать сообщение..." v-model="el.msge"></textarea>
            <a v-if="el.msge.length > 0 " href="#!" class="chat__block-photo" @click="addMessage(el.id,el.msge)" ><img src="../assets/img/svg/send.svg" alt=""></a>
            <a  v-else-if="el.msge == 0 " href="#!" class="chat__block-photo" @click="openImg(el.id)"><img src="../assets/img/svg/photo.svg"  alt=""></a>
          </div>
    </div>
  </div>
    <Source
    :arr="arr"
    v-show="open"
    :idImg="idImg"
    @close="open = false"
    @getInfo="getInfo"
    />
</template>

<script>

import Source from '@/components/Source.vue'

export default {
  components:{
    Source
  },
  props:{
    arr:Array,
    users:Array
  },
  data(){
    return{
        idImg:[],
        imgFile:'',
        img:false,
        status:'',
        open:false,
        styleOne:'chat__block-my message',
        styleTwo:'chat__block-your message',
        message:'',
    }
  },
  methods:{
    addMessage(id,mesage){
        if(mesage != ''){
            const replys = {
              id: id,
              message : mesage,
              date : new Date().toLocaleTimeString(navigator.language, {hour: '2-digit',minute:'2-digit'})
            }
            this.arr.push(replys);
            this.users.forEach(el => el.msge = '')
            console.log(this.arr);
        }
    },
    getStatus(id,message){
      if(id == 1){
        message != '' ? this.users[1].status = 'печатает...' : this.users[1].status = 'в сети'
      }else {
        message != '' ? this.users[0].status = 'печатает...' : this.users[0].status = 'в сети'
      }
    },
    openImg(id){
      this.idImg.push(id);
      this.open = true
      document.body.classList.add('active')
    },
    getInfo(info){
      if(info.img != ''){
        const url = {
          id:info.id,
          img:info.img,
          message:info.mesage,
          date : new Date().toLocaleTimeString(navigator.language, {hour: '2-digit',minute:'2-digit'})
        }
        this.arr.push(url);
      }
    }
  }
}
</script>

<style>
</style>