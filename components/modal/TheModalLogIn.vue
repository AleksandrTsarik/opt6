<template>
  <teleport to="body">
    <div class="modal">
      <div class="modal__overlay"></div>
      <div class="modal__wrap">
        <form action="">
          <div class="modal__form">
            <div class="modal__close" @click="closeModal"></div>
            <div class="modal__title">Авторизация</div>
            <div class="modal__input">
              <UITheInput :type="'email'" :title="'Эл. полчта'" />
              <UITheInput :type="'text'" :title="'Пароль'" />
            </div>
            <div class="modal__btn">
              <UITheButton
                :label="'Войти'"
                class="btn-dark"
              />
            </div>
          </div>
        </form>
      </div>
    </div>
  </teleport>
</template>

<script>
export default {
  props: {
    type: String,
    default: ''
  },
  methods: {
    closeModal() {
      this.$emit('close', false)
    }
  },
}
</script>

<style lang="scss">

</style>