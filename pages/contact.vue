<template>
  <div class="wrapper">
    <TheBreadCrumbs :breadCrumbs="breadCrumbs" />
    <h2 class="title">Contact</h2>
  </div>
</template>

<script>
export default {
  data() {
    return {
      breadCrumbs: [
        {
          name: 'Контакты',
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