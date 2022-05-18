<template>
  <div className="p-3 mb-2 bg-light text-dark container">
    <h1 className="white-text">TabComponent</h1>

    <div class="tabsPane">
      <div className="p-3 mb-2 bg-light text-dark">
        <TabContent
          v-for="tabButton, i in tabButtons"
          :key="i"
          :index="i"
          :text="tabButton"
          @onChange="(val) => updateContent(val)"
        />
      </div>
    </div>
  </div>
  <div>
    {{ content[i] }}
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import TabContent from "./TabContent.vue";


    function updateContent(val: number) {
        console.log("mudou")
        i.value = val;
    }
    defineProps<{
    tabButtons: string[];
    content: string[];
    }>();
    const i = ref(0);

</script>
