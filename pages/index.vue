<template>
  <div>
    <div class="text-center mt-24">
      <h1 class="text-3xl font-bold text-gray-900">ワンチャンまとめ</h1>
      <p class="text-gray-700 mb-1">広告のようなもの</p>
      <Advertising />
      <Button class="mt-8" />
      <h2 class="text-xl font-bold mt-12">みんなのプロジェクト</h2>
      <PostList class="mt-2" />
    </div>
  </div>
</template>

<script>
import Button from '~/components/partials/Button'
import Advertising from '~/components/partials/Advertising'
import PostList from '~/components/partials/PostList'
export default {
  components: {
    Button,
    Advertising,
    PostList
  }
}
</script>

