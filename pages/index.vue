<template>
    <div class=" w-full h-full  bg-[#1F1E1E]" style="
            background-image: url('/images/background.png');
            background-repeat: no-repeat;
            background-size: cover;
            backdrop-filter: blur(2px);
        ">
       <!-- Header -->
         <Header />
       <!-- Content -->
       
        <div class=" w-full h-full  bg-[#1F1E1E] bg-opacity-95 px-4" >
        <!-- First Section -->

           <section class=" w-full max-w-[1568px] m-auto flex items-center md:flex-row flex-col md:justify-between pt-10">
            <div class=" w-full max-w-[530.38px] flex flex-col items-start space-y-6">
                <div>
                    <span class=" text-white font-extrabold font-montserrat text-[50px] md:text-[70px] italic leading-[63px]">BUY ONE,</span><br>
                    <span class=" text-white font-extrabold font-montserrat text-[50px] md:text-[70px] italic leading-[63px]"> GET ONE...</span> <br>
                    <span class="text-[#FC9D0F] font-black font-anybody text-[50px] md:text-[70px] leading-[63px]">EVERYTIME</span>
                </div>
            <button class=" flex items-center space-x-4 rounded-full py-2 px-6 bg-[#FC9D0F] ring-[1px] ring-white hover:bg-opacity-70 hover:ring-0">
                <span class=" text-white text-lg md:text-xl font-poppins font-medium">Download the Extension </span>
                <DownloadIcon />
            </button>
            </div>
            <div class=" w-full max-w-[856px]">
                <img src="/images/cntrls.svg" class=" w-full h-full" alt="">
            </div>
           </section>

        <!-- Second Section -->

        <section class=" w-full h-full md:pt-10">
            <div class=" w-full max-w-[1731px] py-40  m-auto">
                 <div class=" w-full grid grid-cols-1 gap-y-4 md:gap-y-0 md:grid-cols-2 md:gap-x-2 ">
                    <div class="w-full col-spa">
                        <ScrollContainer @scroll="scroll"  />
                    </div>
                    <div class=" w-full ">
                        <span class=" text-white font-black font-montserrat italic text-[28px] md:text-[32px]">HOW IT WORKS</span>
                        <div class=" w-full px-10 pt-16 flex flex-col items-start space-y-10">
                            <div @click="setActive(0)" :class="{'px-10 py-5 w-full border-[3px] border-[#FC9D0F] bg-black': activeIndex === 0,'px-4 py-2 bg-[#7B7D7F] rounded-lg': activeIndex != 0}">
                                <span class=" font-bold text-white font-montserrat text-[22px] md:text-[26px] ">An experience created by you.</span>
                                <div class=" text-white text-xs md:text-base font-montserrat font-normal pl-5" v-if="activeIndex === 0">
                                    Stores and rewards based on your choice.
                                </div>
                            </div>
                              <div @click="setActive(1)" :class="{'px-10 py-5 w-full border-[3px] border-[#FC9D0F] bg-black': activeIndex === 1,'px-4 py-2 bg-[#7B7D7F] rounded-lg': activeIndex != 1}">
                                <span class=" font-bold text-white font-montserrat text-[22px] md:text-[26px] ">Don't waste time by waiting for the right time.</span>
                                <div class=" text-white text-xs md:text-base font-montserrat font-normal pl-5" v-if="activeIndex === 1">
                                    No more saving products for later or waiting for price drops, If you love it, buy it!
                                </div>
                            </div>
                             <div @click="setActive(2)" :class="{'px-10 py-5 w-full border-[3px] border-[#FC9D0F] bg-black': activeIndex === 2,'px-4 py-2 bg-[#7B7D7F] rounded-lg': activeIndex != 2}">
                                <span class=" font-bold text-white font-montserrat text-[22px] md:text-[26px] ">With Kudos, every purchase is a joyful experience.</span>
                                <div class=" text-white text-xs md:text-base font-montserrat font-normal pl-5" v-if="activeIndex === 2">
                                    Shop smarter, shop with kudos!
                                </div>
                            </div>
                        </div>
                    </div>
                 </div>
            </div>
        </section>

        <!-- Third Section -->

        <section class=" w-full flex flex-col items-center  md:pt-10">
            <div class=" flex flex-col items-start space-y-4">
                <p class=" max-w-[679px] text-white font-black font-montserrat italic text-[30px] md:text-[50px] leading-[45px]">
                    <span class=" text-[#FC9D0F]">BUY</span> PRODUCTS YOU LOVE, <span class="text-[#FC9D0F]">REDEEM</span> PRODUCTS TO <span class="text-[#FC9D0F]">BRAG</span> ABOUT.
                </p>
                <button class=" flex items-center space-x-4 rounded-full py-2 px-6 bg-[#FC9D0F] ring-[1px] ring-white hover:bg-opacity-70 hover:ring-0">
                    <span class=" text-white text-lg md:text-xl font-poppins font-medium">Download the Extension </span>
                    <DownloadIcon />
                </button>
            </div>
            <div class=" text-white text-[30px] md:text-[50px] font-black font-montserrat italic text-center pb-10 pt-40">
                <span class=" text-[#FC9D0F]">xxxx users </span> have received rewards
            </div>
        </section>

          
        </div>
       
    </div>
</template>

<script>
import Header from '~/components/Header.vue'
import DownloadIcon from '~/components/icons/DownloadIcon.vue'
import ScrollContainer from '~/components/ScrollContainer.vue'
export default {
    components: {
        Header,
        DownloadIcon,
        ScrollContainer
    },
    data(){
        return{
            activeIndex:0,
        }
    },
    methods:{
        scroll(e){
            if(e == 'first'){
                this.activeIndex = 0
            }else if(e == 'second'){
                this.activeIndex = 1
            }
            else if(e == 'third'){
                this.activeIndex = 2
            }
        },
    }
   
    
}
</script>