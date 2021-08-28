<template>
  <label :class="{ active: isActive }" class="toggle-button">
    <span v-if="isActive">{{ enableText }}</span>
    <span v-if="!isActive">{{ disabledText }}</span>

    <input type="checkbox" :disabled="disabled" v-model="checkedValue" />
    <span class="toggle-switch"></span>
  </label>
</template>

<script>
export default {
  data() {
    return {
      currentState: this.defaultState,
    };
  },
  props: {
    disabled: {
      type: Boolean,
      default: false,
    },
    labelEnableText: {
      type: String,
      default: "INVERT ON",
    },
    labelDisableText: {
      type: String,
      default: "INVERT OFF",
    },
  },
  computed: {
    isActive() {
      return this.currentState;
    },
    enableText() {
      return this.labelEnableText;
    },
    disabledText() {
      return this.labelDisableText;
    },
    checkedValue: {
      get() {
        return this.currentState;
      },
      set(newValue) {
        this.currentState = newValue;
        this.$emit("change", newValue);
      },
    },
  },
};
</script>

<style scoped>
span {
  letter-spacing: 1px;
  font-size: 0.85rem;
}

.toggle-button {
  user-select: none;
  cursor: pointer;
}

/* hides the checkbox */
.toggle-button input[type="checkbox"] {
  opacity: 0;
  position: absolute;
}

.toggle-button .toggle-switch {
  display: inline-block;
  height: 13px;
  border-radius: 6px;
  width: 40px;
  background: #bfcbd9;
  box-shadow: inset 0 0 1px #bfcbd9;
  position: relative;
  margin-left: 10px;
  transition: all 0.2s;
}

.toggle-button .toggle-switch::after,
.toggle-button .toggle-switch::before {
  content: "";
  position: absolute;
  display: block;
  height: 20px;
  width: 20px;
  border-radius: 50%;
  left: 0;
  top: -4px;
  transform: translateX(0);
  transition: all 0.25s cubic-bezier(0.5, -0.6, 0.5, 1.6);
}

.toggle-button .toggle-switch::after {
  background: #4d4d4d;
}

.toggle-button .toggle-switch::before {
  opacity: 0;
}

.active .toggle-switch {
  background: #dcf2de;
}

.active .toggle-switch::after {
  left: 20px;
  background: #009183;
}
</style>
