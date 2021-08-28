<template>
  <div
    class="block"
    v-on:click="toggleBlockBg"
    :class="[blockOfElements, { theme : changeBlockBg }]"
  >
    <span class="element-atomicNumber">
      {{ element.atomicNumber }}
    </span>
    <span class="element-symbol">
      {{ element.symbol }}
    </span>
    <span class="element-name">
      {{ element.name }}
    </span>
  </div>
</template>

<script>
export default {
  props: {
    element: {
      default: function () {
        return {};
      },
    },
    changeBlockBg: {
      type: Boolean,
    },
  },
  computed: {
    blockOfElements() {
      return `block-${this.element.block}`;
    },
  },
  methods: {
    toggleBlockBg() {
      this.$emit("clickedBlock");
    },
  },
};
</script>

<style scoped>
.block {
  cursor: pointer;
  width: 80px;
  height: 70px;
  position: relative;
  transition: all 300ms;
  padding: 1px;
}

.element-atomicNumber {
  font-size: 1rem;
  float: left;
  padding: 0.25rem;
  font-weight: 700;
}

.element-symbol {
  float: right;
  padding: 0.25rem;
  font-size: 1rem;
  font-weight: 700;
}

.element-name {
  letter-spacing: 1px;
  margin: 0;
  position: absolute;
  top: 50%;
  left: 50%;
  -ms-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
  font-size: 0.65rem;
  font-weight: 500;
}

/*  BLOCKS THEME */
.block-s {
  border: black 1px solid;
  color: black;
}

.block-p {
  border: #d23a3f 1px solid;
  color: #d23a3f;
}

.block-d {
  border: #bf9106 1px solid;
  color: #bf9106;
}

.block-f {
  border: #009183 1px solid;
  color: #009183;
}

.theme {
  background: #5D6C8C;
  border: 1px solid white;
  color: #DCF2DE;
}
</style>
