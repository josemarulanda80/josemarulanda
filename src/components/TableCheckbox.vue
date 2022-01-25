<template>
  <div>
    <table class="table table-dark">
      <thead>
        <tr>
          <th scope="col">
            <input
              type="checkbox"
              class="m-2"
              id="checkedOne"
              v-model="checkedOne"
              v-on:change="filterStatesCheckbox"
            />
            <i class="bi bi-file-earmark-plus" style="text-color: gree"></i>
          </th>
          <th scope="col">
            <input
              type="checkbox"
              class="m-2"
              id="chekedTwo"
              v-model="checkedTwo"
              v-on:change="filterStatesCheckbox"
            />
            <i class="bi bi-person"></i>
          </th>
          <th scope="col">
            <input
              type="checkbox"
              class="m-2"
              id="checkedThree"
              v-model="checkedThree"
              v-on:change="filterStatesCheckbox"
            />
            <i class="bi bi-diagram-2"></i>
          </th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="state in stateCheckbox" :key="state">
          <td>
            <i :class="state.icon" :style="{ color: state.colorIcon }"></i>
          </td>
          <td>{{ state.name }}</td>
          <td>
            <input
              class="form-control border border-secondary"
              type="number"
              v-model="state.number"
            />
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "TableCheckbox",
  data() {
    return {
      checkedOne: false,
      checkedTwo: false,
      checkedThree: false,

      stateCheckbox: [],
      stateCheckboxAux: [
        {
          number: "16",
          name: "box_corners",
          cosa: "oto1",
          icon: "bi bi-diagram-2",
          colorIcon: "#FF9900",
        },
        {
          number: "30",
          name: "box_corners",
          cosa: "Thornton2",
          icon: "bi bi-diagram-2",
          colorIcon: "#336600",
        },
        {
          number: "33",
          name: "box_corners",
          cosa: "oto1",
          icon: "bi bi-diagram-2",
          colorIcon:"#FF9900",
        },
        {
          number: "43",
          name: "bounding box",
          cosa: "Thornton2",
          icon: "bi bi-file-earmark-plus",
          colorIcon:  "#9933CC",
        },
        {
          number: "44",
          name: "bounding box",
          cosa: "Larry3",
          icon: "bi bi-file-earmark-plus",
          colorIcon: "#336600",
        },
        {
          number: "46",
          name: "person box",
          cosa: "ddd",
          icon: "bi bi-person",
          colorIcon: "#FF9900",
        },
      ],
    };
  },
  mounted() {
    this.filterStatesCheckbox();
  },
  methods: {
    filterStatesCheckbox() {
      if (
        this.checkedOne == false &&
        this.checkedTwo == false &&
        this.checkedThree == false
      ) {
        this.stateCheckbox = [];
      } else if (
        this.checkedOne == true &&
        this.checkedTwo == true &&
        this.checkedThree == true
      ) {
        this.stateCheckbox = this.stateCheckboxAux;
      } else if (
        this.checkedOne == true &&
        this.checkedTwo == false &&
        this.checkedThree == false
      ) {
        this.stateCheckbox = this.stateCheckboxAux.filter((el) => {
          return el.name == "bounding box";
        });
      } else if (
        this.checkedOne == true &&
        this.checkedTwo == true &&
        this.checkedThree == false
      ) {
        this.stateCheckbox = this.stateCheckboxAux.filter((el) => {
          return el.name == "bounding box" || el.name == "person box";
        });
      } else if (
        this.checkedOne == true &&
        this.checkedTwo == false &&
        this.checkedThree == true
      ) {
        this.stateCheckbox = this.stateCheckboxAux.filter((el) => {
          return el.name == "box_corners" || el.name == "bounding box";
        });
      } else if (
        this.checkedOne == false &&
        this.checkedTwo == true &&
        this.checkedThree == true
      ) {
        this.stateCheckbox = this.stateCheckboxAux.filter((el) => {
          return el.name == "box_corners" || el.name == "person box";
        });
      } else if (
        this.checkedOne == false &&
        this.checkedTwo == true &&
        this.checkedThree == false
      ) {
        this.stateCheckbox = this.stateCheckboxAux.filter((el) => {
          return el.name == "person box";
        });
      } else {
        this.stateCheckbox = this.stateCheckboxAux.filter((el) => {
          return el.name == "box_corners";
        });
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.form-control {
  background-color: #212532;
  color: #fff;
  width: 12vh;
}
</style>
