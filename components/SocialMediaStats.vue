<template>
  <div
    class="rounded-3xl overflow-hidden flex flex-col bg-white border border-gray-300 shadow-xl"
  >
    <div class="p-5 bg-white w-full">
      <div
        class="flex w-10 h-10 justify-center mx-auto mb-3 items-center rounded-xl bg-purple-200"
      >
        <img src="/img/icon/feather_twitter.svg" class="w-28" alt="" />
      </div>
      <p class="text-center text-lg text-purple-700 font-bold mb-6">
        Twitter Stats
      </p>
      <div class="flex justify-between">
        <div>
          <p class="text-sm text-gray-700 font-bold">780318</p>
          <span class="text-gray-600 text-xs">Follower count</span>
        </div>
        <div class="text-right">
          <p class="text-sm text-gray-700 font-bold">2919</p>
          <span class="text-gray-600 text-xs">Stattus count</span>
        </div>
      </div>
    </div>
    <div class="p-5 bg-purple-600 w-full">
      <div
        class="flex w-10 h-10 justify-center mx-auto mb-3 items-center rounded-xl bg-purple-200"
      >
        <img
          src="/img/icon/ant-design_reddit-outlined.svg"
          class="w-28"
          alt=""
        />
      </div>
      <p class="text-center text-lg text-white font-bold mb-6">Reddit Stats</p>
      <div class="flex justify-between">
        <div>
          <p class="text-sm text-white font-bold">3223.65</p>
          <span class="text-purple-200 text-xs">Average Active Users</span>
        </div>
        <div class="text-right">
          <p class="text-sm text-white font-bold">716444</p>
          <span class="text-purple-200 text-xs">Subscribers</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SocialMediaStats',
}
</script>

<style></style>
