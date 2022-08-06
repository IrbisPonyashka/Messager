<template>
  <div class="source">
    <div class="source__item">
        <h2 class="source__item-title">Отправить картинку</h2>
        <div class="source__item-inputs">
          <label>
            <span>URL</span>
            <input v-model="img" type="text" />
          </label>
          <label>
            <span>Комментарий</span>
            <textarea v-model="descr"></textarea>
          </label>
        </div>
        <div class="source__item-btns">
          <button class="source__item-btn cancel" @click="close" >
            Отмена
          </button>
          <button class="source__item-btn send" @click="getInfo">Отправить</button>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  props:{
    arr:Array,
    idImg:Array
  },
  data(){
    return{
      open:true,
      img : '',
      descr: ''
    }
  },
  methods:{
    close(){
      this.$emit('close')
      document.body.classList.remove('active')
    },
    getInfo(){
      if(this.img != ''){
        const info = {
          id: this.idImg[this.idImg.length-1],
          img : this.img,
          mesage : this.descr
        }
        this.img = this.descr = ''
        this.close()
        this.$emit('getInfo',info)
      }
    }
  }

}
</script>

<style>

</style>