<template>
  <div class="wrapper">
    <div class="chat">
    <ChatTwo
    :users="users"
    :arr="arr"
    />
    </div>
  </div>
</template>

<script>

import ChatTwo from '@/components/ChatTwo.vue'

export default {
  components:{
    ChatTwo,
  },
  data(){
    return{
      bool: false,
      clas:'active',
      users:[
        {id:1,name:'Володимиир Путин',img:'putin.jpg',msge:'',status:'в сети'},
        {id:2,name:'Володимир Зеленьский',img:'Zelen.jpg',msge:'',status:'в сети'}
      ],
      arr:[]
    }
  },
  methods:{
    replys(mesge){
      console.log(mesge);
    },
  }
}
</script>

<style>
  body{
    background: #657fa8;
  }
  body::-webkit-scrollbar{
    width: 0px;
  }
  .active{
    overflow: hidden;
  }
</style>