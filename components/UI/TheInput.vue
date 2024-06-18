<template>
  <div v-if="type === 'text'" class="block-input">
    <label>
      <span v-if="title">{{ title }}</span>
      <input type="text" :name="name" v-model="modelValue" @input="$emit('update:modelValue', $event.target.value)">
    </label>
  </div>
  <div v-else-if="type === 'tel'" class="block-input">
    <label>
      <span v-if="title">{{ title }}</span>
      <input type="tel" :name="name" v-model="modelValue" @input="$emit('update:modelValue', $event.target.value)">
    </label>
  </div>
  <div v-else-if="type === 'email'" class="block-input">
    <label>
      <span v-if="title">{{ title }}</span>
      <input type="email" :name="name" v-model="modelValue" @input="$emit('update:modelValue', $event.target.value)">
    </label>
  </div>
</template>

<script>
export default {
  props: {
    modelValue: {
      type: [String, Number],
      default: ''
    },
    label: {
      type: String,
      default: ''
    },
    name: {
      type: String,
      default: ''
    },
    title: {
      type: String,
      default: ''
    },
    type: {
      type: String,
      defrault: '',
      require: true
    }
  },
  data() {
    return {
      modelValue: ''
    }
  },
  methods: {
  },
}
</script>

<style lang="scss">
.block-input {
  width: 100%;
  &.error-field {
    input {
      border-color: red;
    }
  }
  label {
    display: block;
  }
  input {
    padding: 0 10px;
    height: 40px;
    line-height: 40px;
    width: 100%;
    border: solid 1px #BCBCBC;
    border-radius: 6px;
    font-size: 16px;
    position: relative;
    &:focus {
      box-shadow: 0 0 4px rgba(#000, 0.3);
    }

  }
  span {
    font-size: 12px;
    color: #000;
    margin-bottom: 5px;
    display: block;
  }
}
</style>