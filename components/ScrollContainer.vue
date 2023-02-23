<template>
  <div class="w-full">
   <div class=" w-full h-full max-w-[884px] max-h-[133px] pr-[22px]">
    <BrowserHeader />

   </div>

    <div class=" w-full max-h-[477.07px] overflow-y-auto h-full pr-[12px]  max-w-[920px]  space-y-10">
       <div class="w-full bg-[#050608] max-w-[884px] space-y-10 ">
         <div class=" w-full flex flex-col items-center space-y-8 py-10 px-14" id="first">
            <div class=" w-full flex items-start justify-between flex-wrap  md:max-w-[165px] m-auto lg:max-w-full sm:max-w-full max-w-[165px]">
                <div class=" w-full h-full  max-w-[165px] max-h-[202px]">
                    <img src="/images/box.png" class=" w-full h-full" alt="">
                </div>
                 <div class=" w-full h-full max-w-[165px] max-h-[202px]">
                    <img src="/images/nike.png" class=" w-full h-full" alt="">
                </div>
                 <div class=" w-full h-full max-w-[165px] max-h-[202px]">
                    <img src="/images/csk.png" class=" w-full h-full" alt="">
                </div>
            </div>
            <div class=" w-full flex items-center space-x-5 bg-black border border-[#FC9D0F] rounded-lg py-2 px-8 max-w-[644px]" style="box-shadow: 0px 8px 8px 8px rgba(0, 0, 0, 0.25);">
              <div>
                <img src="/images/key.png" class="w-[50px] h-[50px] lg:w-[70px] lg:h-[70px]" alt="">
              </div>
              <span class=" text-lg md:text-2xl font-black font-montserrat italic text-white">Unlock <span class=" text-[#FC9D0F]">your</span> shopping freedom</span>
            </div>
         </div>
          <div class=" w-full flex flex-col items-center space-y-2 py-10 px-14" id="second">
            <div class="">
                <div class=" w-full h-full  max-w-[240px] max-h-[240px]">
                    <img src="/images/cump.png" class=" w-full h-full" alt="">
                </div>
            </div>
            <div class=" w-full flex items-center space-x-5 bg-black border border-[#FC9D0F] rounded-lg py-2 px-8 max-w-[644px]" style="box-shadow: 0px 8px 8px 8px rgba(0, 0, 0, 0.25);">
              <div>
                <img src="/images/bgc.png" class=" w-[50px] h-[50px] lg:w-[80px] lg:h-[80px]" alt="">
              </div>
              <span class=" text-lg md:text-2xl font-black font-montserrat italic text-white">Rewarding <span class=" text-[#FC9D0F]">every</span>purchase</span>
            </div>
         </div>
         <div class=" w-full flex flex-col items-center space-y-2 py-10 px-14" id="third">
            <div class="">
                <div class=" w-full h-full  max-w-[240px] max-h-[240px]">
                    <img src="/images/lbox.png" class=" w-full h-full" alt="">
                </div>
            </div>
            <div class=" w-full flex items-center space-x-5 bg-black border border-[#FC9D0F] rounded-lg py-2 px-8 max-w-[644px]" style="box-shadow: 0px 8px 8px 8px rgba(0, 0, 0, 0.25);">
              <div>
                <img src="/images/book.png" class="w-[50px] h-[50px] lg:w-[80px] lg:h-[80px]" alt="">
              </div>
              <span class=" text-lg md:text-2xl font-black font-montserrat italic text-white">Shop <span class=" text-[#FC9D0F]">smarter</span>, not harder</span>
            </div>
         </div>
       </div>
    </div>
  </div>
</template>


<script>
import BrowserHeader from '~/components/BrowserHeader.vue'
export default {
  data(){
    return {
      active: false,
    }
  },
    components: {
        BrowserHeader
    },
    methods:{
      ScrollTo(id){
        document.getElementById(id).scrollIntoView({behavior: "smooth", block: "start", inline: "nearest"});
         this.active = false
        let time =   setTimeout(() => {
            this.active = true
            clearTimeout(time)
          }, 100);
        
      }
    },
    mounted(){
      const options = {
        root: null,
        rootMargin: '0px',
        threshold: 0.5
      }
      const observer = new IntersectionObserver((entries, observer) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            if(entry.target.id == 'first'){
             if(this.active){
               this.$emit('scroll', 'first')
             }
            }
            if(entry.target.id == 'second'){
              if(this.active){
                this.$emit('scroll', 'second')
              }
            }
            if(entry.target.id == 'third'){
               if(this.active){
                this.$emit('scroll', 'third')
               }
            }
          }
        })
      }, options)
      observer.observe(document.querySelector('#first'))
      observer.observe(document.querySelector('#second'))
      observer.observe(document.querySelector('#third'))
      setTimeout(() => {
        this.active = true
      }, 100);


    }
    
}
</script>



<style scoped>
::-webkit-scrollbar {
  width: 10px;
  border-radius: 10px;
}
::-webkit-scrollbar-track {
  background: #D9D9D9;
    border-radius: 10px;

}
::-webkit-scrollbar-thumb {
  background: #FC9D0F;
    border-radius: 10px;

}
::-webkit-scrollbar-thumb:hover {
  background: #e29d35;
    border-radius: 10px;

}

</style>