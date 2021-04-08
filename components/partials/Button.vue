<template>
  <div>
    <!-- <p class="text-sm text-gray-600">サクッと始めれる</p>
    <p class="text-gray-700 mb-1">あなたも継続してみよう</p> -->
    <button
      class="block mx-auto bg-transparent hover:bg-green-500 text-green-500 font-semibold hover:text-white py-1 px-4 border border-green-500 hover:border-transparent rounded"
      @click="$router.push('/projects/create')"
    >
      <i class="mdi mdi-pencil mr-1" />
      今日のワンチャンを見る
    </button>
  </div>
</template>