<template>
  <v-container
      id="table-set"
      class="pa-0 my-4 mx-auto text--secondary"
      :style="{ width: mobile ? '150px' : '400px', height: mobile ? '150px' : '400px'}"
  >
    <Chair
        id="chair"
        v-for="(member, index) in data.members"
        :key="member"
        :coords="getCoordinates(data.members, index)" :style="{ backgroundColor: data.color || 'lightgrey' }"
        :name="member"
    >
    </Chair>
    <v-responsive
        class="table text-center rounded-circle d-inline-flex align-center justify-center"
        :style="{ backgroundColor: 'lightgrey', height: mobile ? '100%' : '40%', width: mobile ? '100%' : '40%' }">
      <v-row>
        <v-col id="table-name">{{ name }}</v-col>
      </v-row>
      <v-row class="mt-0">
        <v-col>
          <v-img height="40px" contain src="https://cdn-icons-png.flaticon.com/512/898/898087.png"/>
        </v-col>
      </v-row>
    </v-responsive>
  </v-container>
</template>

<script>
import Chair from "@/components/ChairItem";

const outerRadius = 150;
const offset = 200;

function getCoordinates(members, index) {
  const alpha = 2 * Math.PI / members.length * index
  const x = Math.cos(alpha) * outerRadius + offset
  const y = Math.sin(alpha) * outerRadius + offset
  return [x, y]
}

export default {
  name: "TableItem",
  props: ["name", "data"],
  components: {Chair},
  methods: {getCoordinates},
  computed: {
    mobile() {
      return this.$vuetify.breakpoint.sm || this.$vuetify.breakpoint.xs
    },
  }
}
</script>

<style scoped>
#table-set {
  color: black;
  position: relative;
}

#table-name {
  font-size: x-large;
}

.table {
  border: 1px solid grey;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
</style>