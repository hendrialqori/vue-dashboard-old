<script setup>

    import dsh from '../assets/dashboard.svg'
    import pjl from '../assets/Penjualan.svg'
    import master from '../assets/masterdata.svg'
    import user from '../assets/user.svg'
    import report from '../assets/report.svg'
    import out from '../assets/logout.svg'
    import logo from '../assets/logo.svg'

    import { ref, watch } from 'vue'
    import { useRouter } from 'vue-router'

    const refNav = ref(null)
    const isShow = ref(false)
    const router = useRouter()

    const Logout = () => {
        router.push("/login")
    }

    watch(isShow, (current, prev)=> {
        if(current === true) {
            refNav.value.classList.add("translate-y-14")
        }else {
            refNav.value.classList.remove("translate-y-14")
        }
    })

    
    
</script>

<template>
    <div class="text-white p-2 my-5 ml-9 w-max">
        <img :src="logo" alt="logo" width="80">
    </div>
    <nav class="flex flex-col gap-5 font-light text-white">
        <router-link class="flex items-center pl-8 gap-2 text-lg"  to="/">
            <img :src="dsh" alt="dsh-logo">
            Dashboard
        </router-link>
        <router-link class="flex items-center pl-8 gap-2 text-lg"  to="/penjualan">
            <img :src="pjl" alt="dsh-logo">
            Penjualan
        </router-link>
        <div class="text-lg cursor-pointer pl-8 overflow-hidden w-max" >
            <div @click="isShow = !isShow" class="flex items-center gap-2">
                <img :src="master" alt="dsh-logo">
                <p>Master of data</p>
            </div>

            <div ref="refNav" class="flex gap-1 flex-col w-max mt-3 translate-x-8  transition duration-75 ease-linear " aria-label="children-route">
                <router-link class="flex items-center gap-2 text-sm pl-1" to="/user-product">
                    <img :src="user" alt="dsh-logo" width="24">
                    User product
                </router-link>

                <router-link class="flex items-center gap-2 text-sm pl-1" to="/report">
                    <img :src="report" alt="dsh-logo" width="24">
                    Report
                </router-link>
            </div>
        </div>
    </nav>
    <button @click="Logout" class="text-black bg-white text-sm flex gap-1 items-center p-1 rounded-md absolute bottom-7 left-9">
        <img :src="out" alt="" width="24">
        logout
    </button>
</template>

<style>
    .router-link-active {
        border-left: 7px solid gray;
        border-radius: 5px ;
    }
</style>