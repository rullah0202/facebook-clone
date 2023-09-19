<script setup>
import { ref } from 'vue';
import { Link, usePage } from '@inertiajs/vue3';
import Magnify from 'vue-material-design-icons/magnify.vue';
import Home from 'vue-material-design-icons/home.vue';
import HomeOutLine from 'vue-material-design-icons/homeoutline.vue';
import TelevisionPlay from 'vue-material-design-icons/televisionplay.vue';
import StoreFrontOutLine from 'vue-material-design-icons/storefrontoutline.vue';
import AccountGroup from 'vue-material-design-icons/accountgroup.vue';
import ControllerClassicOutline from 'vue-material-design-icons/controllerclassicoutline.vue';
import DotsGrid from 'vue-material-design-icons/dotsgrid.vue';
import FacebookMessenger from 'vue-material-design-icons/facebookmessenger.vue';
import Bell from 'vue-material-design-icons/Bell.vue';
import LogOut from 'vue-material-design-icons/logout.vue';

import CropperModal from '@/Components/CropperModal.vue';
import ImageDisplay from '@/Components/ImageDisplay.vue';
import CreatePostOverlay from '@/Components/CreatePostOverlay.vue';

import { useGeneralStore } from '@/stores/general';
import { storeToRefs } from 'pinia';
const useGeneral = useGeneralStore();
const { isPostOverlay, isCropperModal, isImageDisplay } = storeToRefs(useGeneral);

const user = usePage().props.auth.user;
let showMenu = ref(false);

</script>

<template>
    <div id="MainNav" class="fixed z-50 flex w-full items-center justify-between h-[56px] bg-white shadow-xl border-b">
        <div id="NavLeft" class="flex items-center justify-center w-[260px]">
            <Link  href="/" class="pl-3 min-w-[55px]">
                <img class="w-[40px]" src="/images/icons/FacebookLogoCircle.png">
            </Link>
            <div class="flex items-center justify-center bg-[#EFF2F5] p-1 rounded-full h-[40px] ml-2">
                <Magnify class="p-1" fillColor="#646768" :size="22" />
                <input type="text" placeholder="Search Facebook" class="placeholder-[#646768] bg-[#EFF2F5] border-none p-0 ring-0 focus:ring-0 lg:block hidden">
            </div>  
        </div>
        <div id="NavCenter" class="hidden lg:flex items-center ml-5 justify-center w-8/12 max-w-[600px]">
            <Link href="/" class="w-full">
                <div 
                    :class="$page.url==='/' ? 'mt-1.5' : '' "
                    class="flex items-center justify-center h-[48px] p-1 hover:bg-[#F2F2F2] w-full rounded-lg cursor-pointer">
                    <div>
                        <Home v-if="$page.url==='/'" class="mx-auto text-blue-400" filColor="#1A73E3" :size="27"/>
                        <HomeOutLine v-else class="mx-auto" :size="32" fillColor="#646768"/>
                    </div>
                </div>
                <div v-if="$page.url==='/'" class="border-b-4 border-blue-400 rounded-md">

                </div>
            </Link>
            <button class="flex items-center justify-center h-[48px] p-1 hover:bg-[#F2F2F2] w-full rounded-lg mx-1 cursor-pointer">
                <TelevisionPlay class="mx-auto" filColor="#646768" :size="27"/>
            </button>
            <button class="flex items-center justify-center h-[48px] p-1 hover:bg-[#F2F2F2] w-full rounded-lg mx-1 cursor-pointer">
                <StoreFrontOutLine class="mx-auto" filColor="#646768" :size="27"/>
            </button>
            <button class="flex items-center justify-center h-[48px] p-1 hover:bg-[#F2F2F2] w-full rounded-lg mx-1 cursor-pointer">
                <span class="rounded-full border-[2px] border-[#646768] p-1">
                    <AccountGroup class="mx-auto" filColor="#646768" :size="22"/>
                </span>
            </button>
            <button class="flex items-center justify-center h-[48px] p-1 hover:bg-[#F2F2F2] w-full rounded-lg mx-1 cursor-pointer">
                <ControllerClassicOutline class="mx-auto" filColor="#646768" :size="32"/>
            </button>
        </div>
        <div class="flex w-2/12 items-center justify-end mr-4">
            <button class="rounded-full bg-[#E3E6EA] p-2 hover:bg-gray-300 mx-1 cursor-pointer">
                <DotsGrid :size="23" fillColor="#050505"/>
            </button>
            <button class="rounded-full bg-[#E3E6EA] p-2 hover:bg-gray-300 mx-1 cursor-pointer">
                <FacebookMessenger :size="23" fillColor="#050505"/>
            </button>
            <button class="rounded-full bg-[#E3E6EA] p-2 hover:bg-gray-300 mx-1 cursor-pointer">
                <Bell :size="23" fillColor="#050505"/>
            </button>
            <div class="flex items-center justify-center relative">
                <button @click="showMenu=!showMenu">
                    <img class="rounded-full ml-1 min-w-[40px] max-h-[40px] cursor-pointer" :src="user.image" alt="">
                </button>
                <div v-if="showMenu" class="absolute bg-white shadow-xl top-10 right-0 w-[330px] rounded-lg p-1 border mt-1">
                    <Link :href="route('user.show',{ id : user.id })" @click="showMenu=!showMenu">
                        <div class="flex items-center gap-3 hover:bg-gray-200 p-2 rounded-lg">
                            <img class="rounded-full ml-1 min-w-[35px] max-h-[35px] cursor-pointer" :src="user.image" alt="">
                            <span>{{ user.name }}</span>
                        </div>
                    </Link>
                    <Link class="w-full" :href="route('logout')" as="button" method="post">
                        <div class="flex items-center gap-3 hover:bg-gray-200 px-2 py-2.5 rounded-lg">
                            <LogOut class="pl-2" :size="30"/>
                            <span>Logout</span>
                        </div>
                    </Link>
                    <div class="text-xs font-semibold p-2 pt-3 border-t mt-1">
                        Privacy . Terms . Advertising . Ad Choices . Cookies . Meta &copy; 2023
                    </div>
                </div>
            </div>
        </div>

    </div>
    <slot/>

    <CreatePostOverlay
        v-if="isPostOverlay"
        @showModal = "isPostOverlay=false"
    />
    <CropperModal
        v-if="isCropperModal"
        @showModal = "isCropperModal=false"
    />
    <ImageDisplay
        v-if="isImageDisplay"
    />
</template>
