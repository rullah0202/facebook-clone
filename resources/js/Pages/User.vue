<script setup>
import {Link, Head} from '@inertiajs/vue3';
import MainNavLayout from '@/Layouts/MainNavLayout.vue';
import CreatePostBox from '@/Components/CreatePostBox.vue';
import Post from '@/Components/Post.vue';

import Camera from 'vue-material-design-icons/camera.vue';
import Pen from 'vue-material-design-icons/pen.vue';

import { useGeneralStore } from '@/stores/general';
import { storeToRefs } from 'pinia';

const useGeneral = useGeneralStore();
const { isCropperModal, isImageDisplay } = storeToRefs(useGeneral);

defineProps({posts:Object,user:Object});

</script>
<template>
    <Head>
        <title>User</title>
    </Head>
    <MainNavLayout>
        <div class="w-full min-h-[100vh] pb-20 bg-[#F1F2F5]">
            <div class="w-full bg-white">
                <div class="max-w-[1100px] pt-[56px] mx-auto pb-1">
                    <img class="rounded-b-xl h-[180px] w-full " src="/images/fb-cover-photo.jpg">
                    <div id="ProfileInfo" class="flex md:flex-row flex-col items-center justify-between px-4">
                        <div class="flex md:flex-row flex-col gap-4 md:-mt-6 -mt-16 items-center">
                            <div class="relative">
                                <img class="rounded-full w-[165px] h-[165px] border-white border-4" :src="user.image">
                                <button
                                v-if="$page.props.auth.user.id===user.id"
                                @click="isCropperModal=true" class="absolute right-0 top-[100px] bg-gray-200 hover:bg-gray-300 p-1.5 rounded-full cursor-pointer">
                                    <Camera :size="25"/>
                                </button>
                            </div>
                            <div class="md:mt-4 text-center md:text-left -mt-3">
                                <div class="text-[28px] font-extrabold pt-1">
                                    {{ user.name }}
                                </div>
                                <div class="text-[17px] font-bold text-gray-600 mb-1.5 text-center md:text-left">230 friends</div>
                                <div class="flex md:justify-start justify-center md:-ml-1">
                                    <img class="rounded-full -ml-1 z-[10] w-[40px] h-[40px]" src="/images/friends/1.jpg" alt="">
                                    <img class="rounded-full -ml-3 z-[9] w-[40px] h-[40px]" src="/images/friends/2.jpg" alt="">
                                    <img class="rounded-full -ml-3 z-[8] w-[40px] h-[40px]" src="/images/friends/3.jpg" alt="">
                                    <img class="rounded-full -ml-3 z-[7] w-[40px] h-[40px]" src="/images/friends/4.jpg" alt="">
                                    <img class="rounded-full -ml-3 z-[6] w-[40px] h-[40px]" src="/images/friends/5.jpg" alt="">
                                    <img class="rounded-full -ml-3 z-[5] w-[40px] h-[40px]" src="/images/friends/6.jpg" alt="">
                                    <img class="rounded-full -ml-3 z-[4] w-[40px] h-[40px]" src="/images/friends/7.jpg" alt="">
                                </div>
                            </div>
                        </div>
                        <Link v-if="$page.props.auth.user.id===user.id" :href="route('profile.edit')" class="flex justify-center w-7/12 md:w-[160px] items-baseline md:my-0 my-4 bg-gray-200 hover:bg-gray-300 rounded-lg cursor-pointer">
                            <button class="flex items-center px-5 py-2 font-bold">
                                <Pen class="-ml-2 mr-1" :size="22"/>Edit Profile
                            </button>
                        </Link>
                    </div>
                    <div class="flex border-t h-[50px] py-[4px]">
                        <button class="w-[85px]">
                            <div class="flex items-center text-[15px] justify-center h-[45px] text-blue-500 hover:bg-[#F2F2F2] w-full font-bold rounded-lg cursor-pointer">
                                Posts
                            </div>
                            <div class="border-b-4 border border-b-blue-400 rounded-md"></div>
                        </button>
                        <button class="flex items-center text-[15px] justify-center h-[48px] p-1 hover:bg-[#F2F2F2] w-[85px] font-bold rounded-lg mx-1 cursor-pointer">
                            About
                        </button>
                        <button class="flex items-center text-[15px] justify-center h-[48px] p-1 hover:bg-[#F2F2F2] w-[85px] font-bold rounded-lg mx-1 cursor-pointer">
                            Friends
                        </button>
                        <button class="flex items-center text-[15px] justify-center h-[48px] p-1 hover:bg-[#F2F2F2] w-[85px] font-bold rounded-lg mx-1 cursor-pointer">
                            Videos
                        </button>
                        <button class="flex items-center text-[15px] justify-center h-[48px] p-1 hover:bg-[#F2F2F2] w-[85px] font-bold rounded-lg mx-1 cursor-pointer">
                            Photos
                        </button>
                        <button class="flex items-center text-[15px] justify-center h-[48px] p-1 hover:bg-[#F2F2F2] w-[85px] font-bold rounded-lg mx-1 cursor-pointer">
                            Check-ins
                        </button>
                    </div>
                </div>
            </div>
            <div class="flex-cols md:flex w-full max-w-[1100px] justify-between h-[calc(100vh-56px)] md:px-0 px-2 mx-auto">
                <div id="LeftSection" class="w-full md:w-5/12 mt-4 mr-4">
                    <div class="bg-white p-3 rounded-lg shadow-lg">
                        <div class="font-extrabold pb-2 text-xl">
                            Intro
                        </div>
                        <div class="pb-5">
                            <button class="w-full bg-gray-200 hover:bg-gray-300 rounded-lg p-2 font-bold">
                                Add bio
                            </button>
                        </div>
                        <div class="pb-5">
                            <button class="w-full bg-gray-200 hover:bg-gray-300 rounded-lg p-2 font-bold">
                                Edit details
                            </button>
                        </div>

                        <div class="pb-5">
                            <button class="w-full bg-gray-200 hover:bg-gray-300 rounded-lg p-2 font-bold">
                            Add hobbies
                            </button>
                        </div>
                        <div class="pb-5">
                            <button class="w-full bg-gray-200 hover:bg-gray-300 rounded-lg p-2 font-bold">
                            Add feature
                            </button>
                        </div>
                    </div>
                    <div class="bg-white p-3 mt-4 rounded-lg shadow-lg">
                        <div class="font-extrabold pb-2 text-xl">
                            Photos
                        </div>
                        <div class="flex flex-wrap items-center justify-start w-full">
                            <span v-for="photo in posts.data" :key="photo" class="w-1/3" v-show="photo.image !== null">
                                <img 
                                @click="isImageDisplay= photo.image"
                                class="aspect-square object-cover p-1 rounded-lg cursor-pointer" :src="photo.image">
                            </span>
                        </div>
                    </div>
                </div>
                <div id="PostSection" class="w-full md:w-7/12 overflow-auto">
                    <CreatePostBox
                        v-if="$page.props.auth.user.id===user.id"
                        :image="user.image"
                        :placeholder="`What\'s on your mind ${user.name}`"
                    />
                    <div v-for="post in posts.data" :key="post">
                        <Post :user="post.user" :post="post" :comments="post.comments" />
                    </div>
                </div>
            </div>
        </div>
    </MainNavLayout>
</template>
