<template>
    <div class="bg-gradient-to-r from-cyan-700 to-violet-500
    h-screen
    relative
    flex
    justify-center
    items-center
    ">
        <div class="snap-center
        h-[550px]
        w-[525px]
        bg-white
        rounded-[20px]
        ">
            <h1 class="text-center text-[40px] font-semibold mt-[20px]">Login</h1>
            <div class="border-b pt-6 border-gray-400 mb-7"></div>

            <!-- <form> -->
                <div class="flex justify-center 
                items-center
                ">
                    <input class="pt-[10px] border-b-2 border-gray-400 text-[21px] text-gray-400 w-4/5 focus:outline-0" type="text" placeholder="Username" v-model="user"/>

                </div>
                <div class="flex justify-center 
                items-center
                ">
                    <input class="pt-[60px] border-b-2 border-gray-400 text-[21px] text-gray-400 w-4/5 focus:outline-0" type="password" placeholder="Password" v-model="pass" v-on:keyup.enter="login"/>

                </div>
                <div class="flex justify-center 
                items-center
                ">
                    <p class="pt-[40px] text-gray-400 w-4/5 text-[21px]">Forgot your password?</p>
                </div>
                <div class="flex justify-center 
                items-center pt-9
                ">
                    <button class="bg-cyan-600 rounded-full h-14 font-semibold text-[24px] w-9/12 text-white" @click="login">Login</button>
                
                    <!-- <button @click="login"></button> -->

                </div>
                <div class="flex justify-center 
                items-center pt-9
                ">
                    <p class="text-[24px] text-gray-600">Not a member? </p>
                    <a class="text-[24px] text-cyan-600 ml-2" href="#">Signup</a>
                </div>
            <!-- </form> -->

        </div>
    </div>
</template>

<script setup="ts">

import { ref, onMounted } from 'vue'

const router = useRouter()
const user = ref('')
const pass = ref('')

const login = () => {
    console.log(user, pass, 'test')
    if(user.value == "user" && pass.value == "pass"){
        router.push('/tasks')
        return alert('Login Successfully')

    }
    else {
        return alert('Invalid credentials')
    }
}

</script>