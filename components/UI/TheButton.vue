<template>
  <button
    :type="type"
    class="btn"
  >
    <span v-if="svg" v-html="svg"></span>
    {{ label }}
    <span v-if="time" v-html="time"></span>
  </button>
</template>

<script>
export default {
  props: {
    label: {
      label: String,
      default: '',
      require: true
    },
    type: {
      type: String,
      dafault: ''
    },
    svg: {
      type: String,
      dafault: ''
    },
    time: {
      type: String,
      default: ''
    }
  }
}
</script>

<style lang="scss">
  .btn {
    font-size: 15px;
    font-weight: 400;
    border: solid 1px transparent;
    padding: 9px 14px;
    cursor: pointer;
    border-radius: 5px;
    transition: 0.3s;
    display: inline-block;
    &:active {
      @media(max-width: 1023px) {
        background-color: tomato;
      }
    } 
  }
  .btn-dark {
    background-color: #0584FE;
    color: #fff;
    border: solid 1px transparent;
    @media(min-width: 1024px) {
      &:hover {
        background-color: lighten(#0584FE, 10%);
      }
    }
  }
  .btn-light {
    border: solid 1px #0584FE;
    color: #3C3A3A;
    background-color: #fff;
    @media(min-width: 1024px) {
      &:hover {
        background-color: lighten(#0584FE, 40%);
      }
    }

  }
  .btn-transparent {
    color: #fff;
    background-color: transparent;
    @media(min-width: 1024px) {
      &:hover {
        border-color: #fff;
      }
    }
    @media(max-width: 1023px) {
      border-color: #fff;
    }
  }
</style>