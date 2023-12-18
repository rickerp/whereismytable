<template>
  <v-hover v-slot="{ hover }">
    <v-avatar :size="hover ? 100 : 70"
      class="chair d-none d-md-inline-flex text-center rounded-circle align-center justify-center ma-0 pa-1"
      :style="{ 'top': `${coords[1]}px`, 'left': `${coords[0]}px`, 'font-size': (hover ? '1.2rem' : '1.5rem') }">
      {{ hover ? name : nameInitials(name) }}
    </v-avatar>
  </v-hover>
</template>

<script>
function nameInitials(name) {
  return name.split(' ').filter((w, idx) => idx === 0 || w.length > 3).map(w => w.charAt(0)).join('')
}

export default {
  name: "ChairItem",
  props: ["name", "coords"],
  methods: { nameInitials }
}
</script>

<style scoped>
.chair {
  border: 1px solid grey;
  position: absolute;
  transform: translate(-50%, -50%);
}
</style>