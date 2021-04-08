<template>
    <div>
        <nuxt-link :to="`/advertising`">
            <img width="320" height="320" loading='lazy' class="w-full" :src='this.image' />
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
            res.json().then((response) => {
                const baseUrl = 'https://res.cloudinary.com/kasiwa/image/fetch/f_auto,q_auto,w_320,h_320/'
                this.image = baseUrl + response.message
            })
        })
    }
}
</script>