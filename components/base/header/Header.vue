<template>
  <nav class="grid grid-cols-2 items-center">
    <NuxtLink to="/">
      <img class="w-32" src="~static/icon.png" alt="">
    </NuxtLink>
    <ul v-if="!onMobileCondition" class="grid grid-flow-col justify-self-end gap-x-6">
      <li class="bg-green-300
              hover:bg-gray-50
              border-2
              border-transparent
              hover:border-green-300
              text-center
              w-36
              rounded-2xl
              duration-300 delay-100 ease"
        v-for="mI in m"
          :key="mI.id">
        <NuxtLink class="block py-2 px-3 text-gray-50 hover:text-green-300 duration-300 delay-100 ease" :to="'/' + mI.name">
          {{mI.name}}
        </NuxtLink>
      </li>
    </ul>
    <mobile-menu v-else/>
  </nav>
</template>

<script>
  import MobileMenu from "./MobileMenu";
  // import mixins from "/plugins/mobile-detector.js";
  export default {
    name: "BaseHeader",
    components: {MobileMenu},
    created() {
      if (process.browser) {
        window.addEventListener("resize", this.onResize);
        this.onResize();
      }
    },
    destroyed() {
      if (process.browser) {
        window.removeEventListener("resize", this.onResize);
      }
    },
    data(){
      return {
        onMobileCondition: false,
        m: [{id: 12, name:'about'}, {id: 22, name:'blog'}, {id: 929, name: 'contact'}]
      }
    },
    methods: {
      onResize() {
        this.onMobileCondition = window.innerWidth <= 768;
      }
    }
  }
</script>

<style scoped>
  a.nuxt-link-active {
    font-weight: bold;
  }
</style>
