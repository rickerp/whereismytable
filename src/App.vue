<template>
  <v-app>
    <TopBar/>
    <v-main>
      <v-container style="width: 350px">
        <v-autocomplete
            class="mt-6"
            auto-select-first
            clearable
            rounded
            solo
            :items="members"
        />
      </v-container>
      <v-row class="mb-6">
        <v-col
            v-for="(values, name, index) in tables"
            :key="name" :cols="(index+1) % 3 === 0 ? 12 : 6"
            class="d-flex justify-content-center text-center pa-0"
        >
          <TableItem :name="name" :data="values"/>
        </v-col>
      </v-row>
    </v-main>
  </v-app>
</template>

<script>
import TopBar from "@/components/TopBar";
import TableItem from "@/components/TableItem";

import tablesData from "@/assets/tables.json"

export default {
  name: 'App',

  components: {
    TopBar,
    TableItem,
  },

  data: () => ({
    tables: tablesData,
    members: [].concat(...Object.values(tablesData).map(v => v.members)).sort()
  }),
};
</script>

<style>
@font-face {
  font-family: "MarcellusSC";
  src: local("MarcellusSC"),
  url(./assets/MarcellusSC-Regular.ttf) format("truetype");
}
* {
  font-family: "MarcellusSC";
}
</style>