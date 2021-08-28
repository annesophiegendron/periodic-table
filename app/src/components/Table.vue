<template>
  <div>
    <ToggleButton v-on:change="toggleHandler" />
    <table class="wrapper">
      <tr :key="rowIndex" v-for="(rowItems, rowIndex) in items">
        <td :key="columnIndex" v-for="(element, columnIndex) in rowItems">
          <Element
            v-if="element"
            @clickedBlock="colourBlock(element.block)"
            :element="element"
            :changeBlockBg="colouredOnclick[element.block]"
          />
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
import Element from "./Element";
import ToggleButton from "./ToggleButton.vue";

const numberOfRows = 9;
const numberOfColumns = 18;

export default {
  data() {
    return {
      items: [],
      colouredOnclick: {},
      active: false,
    };
  },
  mounted() {
    this.toggleHandler();
  },

  components: {
    Element,
    ToggleButton,
  },
  props: {
    elements: {
      default: function () {
        return [];
      },
    },
  },
  methods: {
    toggleHandler(value) {
      this.active = value;
      this.items = [];
      while (this.items.push(new Array(numberOfColumns)) < numberOfRows);

      if (value == true) {
        this.elements.map((el) => {
          this.items[numberOfRows - el.row][el.column] = el;
        });
      } else {
        this.elements.map((el) => {
          this.items[el.row - 1][el.column] = el;
        });
      }
    },

    colourBlock(el) {
      this.colouredOnclick = { [el]: !this.colouredOnclick[el] };
    },
  },
};
</script>

<style scoped>
.wrapper {
  margin-top: 20px;
}
</style>
