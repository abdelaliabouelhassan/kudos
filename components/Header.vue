<template>
     <div class=" w-full bg-[#000000] flex items-center justify-between px-7 py-10">
            <!-- Logo -->
            <div class=" max-w-[303px] max-h-[90px]">
               <a href="#"><Logo /></a>
            </div>
            <!-- Download Button -->
            <button class=" flex items-center space-x-4 rounded-full py-2 px-6 bg-[#FC9D0F] ring-[1px] ring-white hover:bg-opacity-70 hover:ring-0">
                <span class=" text-white text-xl font-poppins font-medium">Download the Extension </span>
                <DownloadIcon />
            </button>
        </div>
</template>


<script>
import Logo from '~/components/icons/Logo.vue'
import DownloadIcon from '~/components/icons/DownloadIcon.vue'
export default {
    components: {
        Logo,
        DownloadIcon
    }
    
}
</script>


