<template>
    <div class="flex justify-center">
        <nuxt-link :to="`/advertising`">
            <!-- <img loading='lazy' class="w-full" :src='this.image' /> -->
            <img class="w-full" :src='this.image' />
        </nuxt-link>
    </div>
</template>

<script>
export default {
    data() {
        return {
            image: ''
        }
    },
    mounted() {
        fetch('https://dog.ceo/api/breeds/image/random').then((res) => {
            console.log(res)
            res.json().then((response) => {
                // const baseUrl = 'https://res.cloudinary.com/kasiwa/image/fetch/f_webp,q_auto,w_320,h_320/'
                // this.image = baseUrl + response.message
                this.image = response.message
            })
            // console.log(res.json())
            // response = res.json()
            // this.image = res.message
            // console.log(res)
            // console.log(this.image)
        })
    }
}
</script>