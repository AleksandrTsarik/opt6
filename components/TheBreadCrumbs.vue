<template>
  <div class="bread-crumbs">
    <div class="bread-crumbs__links">
      <NuxtLink to="/">Главная страница </NuxtLink>
      <div v-for="(item , i) in breadCrumbs" :key="i">
        <NuxtLink v-if="!item.current" :to="item.url"> {{ item.name }} </NuxtLink>
        <span v-else-if="item.current"> {{ item.name }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    breadCrumbs: {
      type: Array,
      dafault: {}
    }

  }
}
</script>

<style lang="scss" scoped>
  .bread-crumbs {
    font-size: 13px;
    color: #212529;
    margin: 20px 0;
    a {
      color: #000;
    }
    &__links {
      display: flex;
      align-items: center;
      flex-wrap: wrap;
      div {
        margin-left: 25px;
        position: relative;
        color: rgba(143, 143, 143, 1);
        &::after {
          content: '';
          display: block;
          width: 5px;
          height: 5px;
          background-color: #000;
          border-radius: 50%;
          position: absolute;
          left: -15px;
          top: 50%;
          transform: translateY(-50%);
        }
      }
    }
  }
</style>