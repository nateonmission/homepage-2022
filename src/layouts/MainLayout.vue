<template>
  <q-layout view="hHh lpR fFf">
    <div class="page">
      <q-page-container>
        <router-view :handle="handle" />
      </q-page-container>
    </div>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from "vue";

import resume from "../../public/data/Resume.json";

const linksList = [];

export default defineComponent({
  name: "MainLayout",

  data() {
    return {
      resume: resume,
      handle: "NateOnMission",
      name: "Nathan Allen",
      role: "Developer",
      email: "nateonmission@gmail.com",
    };
  },

  calculated: {
    getYear() {},
  },

  components: {},

  setup() {
    return {};
  },
});
</script>
