<template>
  <header>
    <div
      class="bg-white shadow border-b border-gray-200 h-12 md:h-16 flex items-center fixed top-0 inset-x-0 z-100"
    >
      <div
        class="mx-auto w-full max-w-screen-lg flex items-center justify-between px-4 py-2"
      >
        <nuxt-link to="/">
          <span class="text-gray-900 font-bold text-sm md:text-lg">
              ワンチャンまとめ
          </span>
        </nuxt-link>
      </div>
    </div>
  </header>
</template>

<script>
export default {

}
</script>

<style scoped>
.z-100 {
  z-index: 100;
}
</style>
