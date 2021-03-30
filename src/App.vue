<template>
  <Map />
  <ToolBarMdb v-if="type === 'mdb'" />
  <ToolBarUI v-if="type === 'ui'" />
  <ToolBarTailwind v-if="type === 'tailwind'" />
  <div class="tool">
    <label v-for="(value, key) in typeObj" :key="key">
      <input type="radio" :value="value" v-model="type" />
      {{ key }}
    </label>
  </div>
</template>

<script>
import { defineAsyncComponent } from "vue";
import Map from "./components/Map.vue";
 import ToolBarMdb from "./widgets/toolbar_Mdb.vue";
import ToolBarUI from "./widgets/toolbar_EleUI.vue";
import ToolBarTailwind from "./widgets/toobar_Tailwind.vue";
// const ToolBarMdb = defineAsyncComponent(() =>
//   import("./widgets/toolbar_Mdb.vue")
// );

export default {
  name: "App",
  components: {
    Map,
    ToolBarMdb,
    ToolBarUI,
    ToolBarTailwind,
  },
  mounted() {},
  data() {
    return {
      type: "ui",
      typeObj: {
        mdb: "mdb",
        ui: "ui",
        tailwind: "tailwind",
      },
    };
  },
};
</script>

<style>
body,
html {
  margin: 0;
  padding: 0;
}
* {
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
}
.tool {
  position: absolute;
  top: 10px;
  left: 60px;
  z-index: 999;
  font-size: 2rem;
  font-weight: 800;
  color: red;
}

label + label {
  margin-left: 5px;
}
</style>
