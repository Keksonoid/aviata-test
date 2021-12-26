<template>
  <label class="checkbox-wrapper d-flex align-center">
    <input
      type="checkbox"
      :value="inputValue"
      v-model="model"
      @change="onChange"
    />
    <span class="checkbox-checkmark"></span>
    <span class="ml-3">{{ label }}</span>
  </label>
</template>

<script>
export default {
  name: "Checkbox",
  props: {
    label: String,
    value: [Array, Boolean],
    inputValue: String,
  },
  computed: {
    model: {
      get() {
        return this.value;
      },
      set(value) {
        this.$emit("input", value);
      },
    },

    isChecked() {
      return typeof this.value === "boolean"
        ? this.value
        : this.value.includes(this.inputValue);
    },
  },
  methods: {
    onChange(val) {
      this.$emit("change", val);
    },
  },
};
</script>

<style lang="scss">
label {
  user-select: none;
}

.checkbox-wrapper {
  cursor: pointer;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  font-size: 14px;
  line-height: 16px;
  padding: 10px 12px;
  &:hover {
    background-color: #ebebeb;
  }
}

.checkbox-checkmark {
  display: inline-block;
  height: 10px;
  width: 10px;
  border: 1px solid #b9b9b9;
  border-radius: 2px;
  background-color: #ffffff;
  transition: background-color 0.4s ease-in-out;
}

.checkbox-wrapper input:hover ~ .checkbox-checkmark {
  background-image: url("../../assets/checbox_hover.svg");
  // border: 0px;
  background-position: center;
  background-repeat: no-repeat;
  // background-size: cover;
  transition: background-image 0.4s ease-in-out;
}

.checkbox-wrapper input:checked ~ .checkbox-checkmark {
  border: 1px solid #55bb06;
  background-image: url("../../assets/checbox-active.svg");
  background-position: center;
  background-repeat: no-repeat;
  transition: background-image 0.4s ease-in-out;
}

.checkbox-wrapper input:checked:hover ~ .checkbox-checkmark {
  background-image: url("../../assets/checbox_indeterminate.svg");
  // border: 0px;
  background-position: center;
  background-repeat: no-repeat;
  // background-size: cover;
  transition: background-image 0.4s ease-in-out;
}

.checkbox-wrapper input {
  display: none;
}
</style>
