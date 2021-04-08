<template>
  <div>
    <ul>
      <li v-for="image in images" :key="image">
        <div class="mb-4">
              <div class="flex justify-center">
                <img loading='lazy' :src="baseUrl + image">
              </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
    data() {
        return {
            images: [],
            baseUrl: 'https://res.cloudinary.com/kasiwa/image/fetch/f_webp,q_auto,w_320,h_320/'
        }
    },
    mounted() {
        fetch('https://dog.ceo/api/breeds/image/random/50').then((res) => {
            res.json().then((response) => {
                console.log(response)
                console.log(response.message)
                this.images = response.message
            })
        })
    }
}
</script>