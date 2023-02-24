<template>
  <div class="w-full rounded-bl-lg overflow-hidden">
   <div class=" w-full h-full max-w-[55.25rem] max-h-[8.313rem] md:pr-[2.3rem]">
    <BrowserHeader />

   </div>

    <div id="scrollContainer" class=" w-full max-h-[29.817rem] overflow-y-auto h-full md:pr-[1.78rem]  rounded-br-lg overflow-hidden  max-w-[57.5rem]  space-y-10">
       <div class="w-full bg-[#050608] max-w-[55.25rem] space-y-10 rounded-br-lg overflow-hidden">
         <div class=" w-full flex flex-col items-center space-y-8 py-10 px-14  rounded-br-lg overflow-hidden" id="first">
            <div class=" w-full flex items-start justify-between flex-wrap  md:max-w-[10.313rem] m-auto lg:max-w-full sm:max-w-full max-w-[10.313rem]">
                <div class=" w-full h-full  max-w-[10.313rem] max-h-[12.625rem]">
                    <img src="/images/box.png" class=" w-full h-full" alt="">
                </div>
                 <div class=" w-full h-full max-w-[10.313rem] max-h-[12.625rem]">
                    <img src="/images/nike.png" class=" w-full h-full" alt="">
                </div>
                 <div class=" w-full h-full max-w-[10.313rem] max-h-[12.625rem]">
                    <img src="/images/csk.png" class=" w-full h-full" alt="">
                </div>
            </div>
            <div class=" w-full flex items-center space-x-5 bg-black border border-[#FC9D0F] rounded-lg py-2 px-8 max-w-[40.25rem]" style="box-shadow: 0px 8px 8px 8px rgba(0, 0, 0, 0.25);">
              <div>
                <img src="/images/key.png" class="w-[3.125rem] h-[3.125rem] lg:w-[4.375rem] lg:h-[4.375rem]" alt="">
              </div>
              <span class=" text-lg md:text-2xl font-black font-montserrat italic text-white">Unlock <span class=" text-[#FC9D0F]  text-lg md:text-2xl">your</span> shopping freedom</span>
            </div>
         </div>
          <div class=" w-full flex flex-col items-center space-y-2 py-10 px-14  rounded-br-lg overflow-hidden" id="second">
            <div class="">
                <div class=" w-full h-full  max-w-[15rem] max-h-[15rem]">
                    <img src="/images/cump.png" class=" w-full h-full" alt="">
                </div>
            </div>
            <div class=" w-full flex items-center space-x-5 bg-black border border-[#FC9D0F] rounded-lg py-2 px-8 max-w-[40.25rem]" style="box-shadow: 0px 8px 8px 8px rgba(0, 0, 0, 0.25);">
              <div>
                <img src="/images/bgc.png" class=" w-[3.125rem] h-[3.125rem] lg:w-[5rem] lg:h-[5rem]" alt="">
              </div>
              <span class=" text-lg md:text-2xl font-black font-montserrat italic text-white">Rewarding <span class=" text-[#FC9D0F]  text-lg md:text-2xl">every</span> purchase</span>
            </div>
         </div>
         <div class=" w-full flex flex-col items-center space-y-2 py-10 px-14  rounded-br-lg overflow-hidden" id="third">
            <div class="">
                <div class=" w-full h-full  max-w-[15rem] max-h-[15rem]">
                    <img src="/images/lbox.png" class=" w-full h-full" alt="">
                </div>
            </div>
            <div class=" w-full flex items-center space-x-5 bg-black border border-[#FC9D0F] rounded-lg py-2 px-8 max-w-[40.25rem]" style="box-shadow: 0px 8px 8px 8px rgba(0, 0, 0, 0.25);">
              <div>
                <img src="/images/book.png" class="w-[3.125rem] h-[3.125rem] lg:w-[5rem] lg:h-[5rem]" alt="">
              </div>
              <span class=" text-lg md:text-2xl font-black font-montserrat italic text-white">Shop <span class=" text-[#FC9D0F]  text-lg md:text-2xl">smarter</span>, not harder</span>
            </div>
         </div>
       </div>
    </div>
  </div>
</template>


<script>
import BrowserHeader from '~/components/BrowserHeader.vue'
export default {
  props:{
    activeIndex:{
      type: [String, Number],
      default: 0,
    },
    activetype:{
      type: [String, Number],
      default: 1,
    }
  },
  data(){
    return {
      active: false,
      timer:null,
      type:1,
    }
  },
    components: {
        BrowserHeader
    },
    methods:{
      ScrollTo(id){
       const scrollContainer = document.getElementById("scrollContainer");
       const target = document.getElementById(id);
       scrollContainer.scrollTo({
          top: target.offsetTop - scrollContainer.offsetTop,
          behavior: 'smooth'
        });
      }
    },
    watch:{
      activeIndex(){
        if(this.activeIndex == 0 && this.type == 0){
          this.ScrollTo('first')
        }
        if(this.activeIndex == 1 && this.type == 0){
          this.ScrollTo('second')
        }
        if(this.activeIndex == 2 && this.type == 0) {
          this.ScrollTo('third')
        }
      },
      //deep:true for activetype
      
      activetype:{
        handler(){
          if(this.activetype == 0){
            this.type = 0
          }
          if(this.activetype == 1){
            this.type = 1
          }
        },
        deep:true
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
      }, 500);


    }
    
}
</script>



<style scoped>
::-webkit-scrollbar {
  width: 0.625rem;
  border-radius: 2rem;
  
}
::-webkit-scrollbar-track {
  background: #D9D9D9;
    border-radius: 2rem;

}
::-webkit-scrollbar-thumb {
  background: #FC9D0F;
    border-radius: 2rem;

}
::-webkit-scrollbar-thumb:hover {
  background: #e29d35;
    border-radius: 2rem;

}

</style>