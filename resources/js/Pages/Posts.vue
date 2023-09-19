<script setup>
import MainNavLayout from '@/Layouts/MainNavLayout.vue';
import CreatePostBox from '@/Components/CreatePostBox.vue';
import Post from '@/Components/Post.vue';
import { Head,usePage,Link } from '@inertiajs/vue3';

import Magnify from 'vue-material-design-icons/magnify.vue';
import TelevisionPlay from 'vue-material-design-icons/televisionplay.vue';
import StoreFrontOutLine from 'vue-material-design-icons/storefrontoutline.vue';
import AccountGroup from 'vue-material-design-icons/accountgroup.vue';
import AccountMultiple from 'vue-material-design-icons/accountmultiple.vue';
import Flag from 'vue-material-design-icons/flag.vue';
import ClockTimeTwoOutline from 'vue-material-design-icons/clocktimetwooutline.vue';
import Restore from 'vue-material-design-icons/restore.vue';
import VideoImage from 'vue-material-design-icons/VideoImage.vue';
import DotsHorizontal from 'vue-material-design-icons/dotshorizontal.vue';

defineProps({posts : Object})

const user = usePage().props.auth.user;
</script>

<template>
    <Head title="Posts" />

    <MainNavLayout>
        <div class="fixed w-full h-[100%] bg-[#F1F2F5]">
            <div class="grid grid-rows-3 grid-flow-col w-full max-w-[1600px] mt-[56px] h-[calc(100%-56px)] mx-auto px-4">
                <div id="LeftSection" class="xl:w-[345px] lg:block hidden">
                    <div class="pt-4 max-w-[320px] pr-4">
                        <Link :href="route('user.show',{id: user.id})" class="flex items-center justify-start w-full cursor-pointer hover:bg-[#E5E6E9] p-2 rounded-md">
                            <img class="rounded-full ml-1 min-w-[38px] max-h-[38px]" :src="user.image">
                            <div class="text-[15px] text-gray-800 font-extrabold pl-3">{{ user.name }}</div>
                        </Link>
                        <button class="flex items-center justify-start w-full cursor-pointer hover:bg-[#E5E6E9] px-2 py-1.5 rounded-md">
                            <AccountMultiple :size="40" fillColor="#5BD7C6"/>
                            <div class="text-[15px] text-gray-800 font-extrabold pl-3">
                                Friends
                            </div>
                        </button>
                        <button class="flex items-center justify-start w-full cursor-pointer hover:bg-[#E5E6E9] px-2 py-1.5 rounded-md">
                            <Flag :size="40" fillColor="#F2C82C"/>
                            <div class="text-[15px] text-gray-800 font-extrabold pl-3">
                                Pages
                            </div>
                        </button>
                        <button class="flex items-center justify-start w-full cursor-pointer hover:bg-[#E5E6E9] px-2 py-1.5 rounded-md">
                            <ClockTimeTwoOutline :size="40" fillColor="#21AAFA"/>
                            <div class="text-[15px] text-gray-800 font-extrabold pl-3">
                                Most Recent
                            </div>
                        </button>
                        <button class="flex items-center justify-start w-full cursor-pointer hover:bg-[#E5E6E9] px-2 py-1.5 rounded-md">
                            <AccountGroup :size="40" fillColor="#20A9FD"/>
                            <div class="text-[15px] text-gray-800 font-extrabold pl-3">
                                Groups
                            </div>
                        </button>
                        <button class="flex items-center justify-start w-full cursor-pointer hover:bg-[#E5E6E9] px-2 py-1.5 rounded-md">
                            <StoreFrontOutLine :size="40" fillColor="#48C0D8"/>
                            <div class="text-[15px] text-gray-800 font-extrabold pl-3">
                                Marketplace
                            </div>
                        </button>
                        <button class="flex items-center justify-start w-full cursor-pointer hover:bg-[#E5E6E9] px-2 py-1.5 rounded-md">
                            <TelevisionPlay :size="40" fillColor="#9739CF"/>
                            <div class="text-[15px] text-gray-800 font-extrabold pl-3">
                                Watch
                            </div>
                        </button>
                        <button class="flex items-center justify-start w-full cursor-pointer hover:bg-[#E5E6E9] px-2 py-1.5 rounded-md">
                            <Restore :size="40" fillColor="#32B4D0"/>
                            <div class="text-[15px] text-gray-800 font-extrabold pl-3">
                                Memories
                            </div>
                        </button>
                    </div>
                </div>
                <div id="PostSection" class="row-span-6 max-w-[600px] lg:mx-0 mx-auto overflow-auto">
                    <CreatePostBox
                        :image="user.image"
                        :placeholder="`What's on your mind ${ user.name }`"
                    />
                    <div v-for="post in posts.data" :key="post">
                        <Post :user="post.user" :post="post" :comments="post.comments" />
                    </div>
                </div>
                <div id="RightSection" class="pl-4 md:block hidden">
                    <div class="max-w-[340px] min-w-[250px] mx-auto pt-4">
                        <div class="flex items-center justify-between border-b border-b-gray-300 p-1">
                            <div class="font-semibold">Contacts</div>
                            <div class="flex items-center">
                                <div class="p-2 hover:bg-gray-300 rounded-full cursor-pointer">
                                    <VideoImage :size="23" fillColor="#050505"/>
                                </div>
                            </div>
                            <div class="flex items-center">
                                <div class="p-2 hover:bg-gray-300 rounded-full cursor-pointer">
                                    <Magnify :size="23" fillColor="#050505"/>
                                </div>
                            </div>
                            <div class="flex items-center">
                                <div class="p-2 hover:bg-gray-300 rounded-full cursor-pointer">
                                    <DotsHorizontal :size="23" fillColor="#050505"/>
                                </div>
                            </div>
                        </div>
                        <div class="h-[calc(100vh-145px)] overflow-auto pt-2">
                            <div class="flex items-center justify-start cursor-pointer hover:bg-[#E5E6E9] py-2 rounded-md">
                                <img class="rounded-full ml-1 min-w-[38px] max-h-[38px]" src="/images/friends/1.jpg" alt="">
                                <div class="text-[15px] text-gray-800 font-extrabold pl-3">Niamat Ullah</div>
                            </div>
                            <div class="flex items-center justify-start cursor-pointer hover:bg-[#E5E6E9] py-2 rounded-md">
                                <img class="rounded-full ml-1 min-w-[38px] max-h-[38px]" src="/images/friends/2.jpg" alt="">
                                <div class="text-[15px] text-gray-800 font-extrabold pl-3">Barkat Ullah</div>
                            </div>
                            <div class="flex items-center justify-start cursor-pointer hover:bg-[#E5E6E9] py-2 rounded-md">
                                <img class="rounded-full ml-1 min-w-[38px] max-h-[38px]" src="/images/friends/3.jpg" alt="">
                                <div class="text-[15px] text-gray-800 font-extrabold pl-3">Shameem Russel</div>
                            </div>
                            <div class="flex items-center justify-start cursor-pointer hover:bg-[#E5E6E9] py-2 rounded-md">
                                <img class="rounded-full ml-1 min-w-[38px] max-h-[38px]" src="/images/friends/4.jpg" alt="">
                                <div class="text-[15px] text-gray-800 font-extrabold pl-3">Inamul Huq</div>
                            </div>
                            <div class="flex items-center justify-start cursor-pointer hover:bg-[#E5E6E9] py-2 rounded-md">
                                <img class="rounded-full ml-1 min-w-[38px] max-h-[38px]" src="/images/friends/5.jpg" alt="">
                                <div class="text-[15px] text-gray-800 font-extrabold pl-3">Nahian</div>
                            </div>
                            <div class="flex items-center justify-start cursor-pointer hover:bg-[#E5E6E9] py-2 rounded-md">
                                <img class="rounded-full ml-1 min-w-[38px] max-h-[38px]" src="/images/friends/6.jpg" alt="">
                                <div class="text-[15px] text-gray-800 font-extrabold pl-3">Opurbo</div>
                            </div>
                            <div class="flex items-center justify-start cursor-pointer hover:bg-[#E5E6E9] py-2 rounded-md">
                                <img class="rounded-full ml-1 min-w-[38px] max-h-[38px]" src="/images/friends/7.jpg" alt="">
                                <div class="text-[15px] text-gray-800 font-extrabold pl-3">Meherima</div>
                            </div>
                            <div class="flex items-center justify-start cursor-pointer hover:bg-[#E5E6E9] py-2 rounded-md">
                                <img class="rounded-full ml-1 min-w-[38px] max-h-[38px]" src="/images/friends/2.jpg" alt="">
                                <div class="text-[15px] text-gray-800 font-extrabold pl-3">Toma</div>
                            </div>
                            <div class="flex items-center justify-start cursor-pointer hover:bg-[#E5E6E9] py-2 rounded-md">
                                <img class="rounded-full ml-1 min-w-[38px] max-h-[38px]" src="/images/friends/5.jpg" alt="">
                                <div class="text-[15px] text-gray-800 font-extrabold pl-3">Orin</div>
                            </div>
                            <div class="flex items-center justify-start cursor-pointer hover:bg-[#E5E6E9] py-2 rounded-md">
                                <img class="rounded-full ml-1 min-w-[38px] max-h-[38px]" src="/images/friends/3.jpg" alt="">
                                <div class="text-[15px] text-gray-800 font-extrabold pl-3">Sarin</div>
                            </div>
                            <div class="flex items-center justify-start cursor-pointer hover:bg-[#E5E6E9] py-2 rounded-md">
                                <img class="rounded-full ml-1 min-w-[38px] max-h-[38px]" src="/images/friends/1.jpg" alt="">
                                <div class="text-[15px] text-gray-800 font-extrabold pl-3">Shefaly Akhter</div>
                            </div>
                            <div class="flex items-center justify-start cursor-pointer hover:bg-[#E5E6E9] py-2 rounded-md">
                                <img class="rounded-full ml-1 min-w-[38px] max-h-[38px]" src="/images/friends/6.jpg" alt="">
                                <div class="text-[15px] text-gray-800 font-extrabold pl-3">Lovely Akhter</div>
                            </div>
                            <div class="flex items-center justify-start cursor-pointer hover:bg-[#E5E6E9] py-2 rounded-md">
                                <img class="rounded-full ml-1 min-w-[38px] max-h-[38px]" src="/images/friends/5.jpg" alt="">
                                <div class="text-[15px] text-gray-800 font-extrabold pl-3">Ariful Islam</div>
                            </div>
                            <div class="flex items-center justify-start cursor-pointer hover:bg-[#E5E6E9] py-2 rounded-md">
                                <img class="rounded-full ml-1 min-w-[38px] max-h-[38px]" src="/images/friends/6.jpg" alt="">
                                <div class="text-[15px] text-gray-800 font-extrabold pl-3">Anisul Islam</div>
                            </div>
                            <div class="flex items-center justify-start cursor-pointer hover:bg-[#E5E6E9] py-2 rounded-md">
                                <img class="rounded-full ml-1 min-w-[38px] max-h-[38px]" src="/images/friends/7.jpg" alt="">
                                <div class="text-[15px] text-gray-800 font-extrabold pl-3">Bazlur Rahman</div>
                            </div>
                            <div class="flex items-center justify-start cursor-pointer hover:bg-[#E5E6E9] py-2 rounded-md">
                                <img class="rounded-full ml-1 min-w-[38px] max-h-[38px]" src="/images/friends/2.jpg" alt="">
                                <div class="text-[15px] text-gray-800 font-extrabold pl-3">Minhaj Uddin</div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </MainNavLayout>
</template>
