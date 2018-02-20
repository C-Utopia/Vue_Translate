<template>



  <div id="music" class="up"  >
     <button @click="show=!show" >音乐</button>
   <transition name="slide-fade">
    
  
  <iframe  v-if="show"  frameborder="no" border="0" marginwidth="0" marginheight="0" width=298 height=52 src="//music.163.com/outchain/player?type=0&id=2080982962&auto=0&height=32"></iframe>
   </transition>
  </div>
</template>
<script>
export default {
  data() {
    return {
      show:true
    };
  },
  methods:{
     
  }

  
};
</script>
<style scoped>
#music {
  position: absolute;
  bottom: 0;
  width: 100%;
 
}
/* 可以设置不同的进入和离开动画 */
/* 设置持续时间和动画函数 */
.slide-fade-enter-active {
  transition: all .8s ease;
}
.slide-fade-leave-active {
  transition: all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}
.slide-fade-enter, .slide-fade-leave-to
 {
  transform: translateY(10px);
  opacity: 0;
}

iframe {
  width: 96%;
  
  
}
button{

position: absolute;
right: 2px;
bottom: 0;
width: 2%;
height: 52px;
border: 0;
background-color: #5bc0de;

 color: #ffffff;
  
  font-size: 12px;
  border-radius: 2px;
  
}
</style>
