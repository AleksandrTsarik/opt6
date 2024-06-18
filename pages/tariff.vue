<template>
  <div class="wrapper">
    <TheBreadCrumbs :breadCrumbs="breadCrumbs" />
    <h2 class="title">Tariff</h2>
  </div>
</template>

<script>
export default {
  data() {
    return {
      breadCrumbs: [
        {
          name: 'Тарифы',
          url: '#',
          current: true
        }
      ]
    }
  }
}
</script>

<style>

</style>