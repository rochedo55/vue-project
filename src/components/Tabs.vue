<template>
  <div>
    <h1>TabComponent</h1>
    <div>
      <div class="tabs">
        <TabContent
          v-for="tabContent, i in tabs_contents"
          :key="i"
          :index="tabContent.id"
          :text="tabContent.title"
          @onChange="(val) => updateContent(val)"
        />
      </div>
    </div>
  </div>
  <br/>
  <div class="content">
    {{ tabs_contents[i].content }}
  </div>
  <div>
    <AddTabVue @onChange="(title,content) => newTab(title,content)"/>
  </div>
</template>

<script setup lang="ts">
import { ref, reactive } from "vue";
import TabContent from "./TabContent.vue";
import AddTabVue from "./AddTab.vue";

    async function newTab(title: string, content: string){
      console.log("chegou");      
      let aux = {
        title: title,
        content: content,
        id: increment()
      }
      tabs_contents.push(aux)
    }

    function increment(){
      return (tabs_contents.length -1) + 1
    }

    function updateContent(val: number) {
        console.log("mudou")
        i.value = val;
    }

    defineProps<{
    tabButtons: string[];
    content: string[];
    }>();

    const i = ref(0);

    let tabs_contents = reactive([{
      id: 0,
      content: "Lorem Ipsum é simplesmente uma simulação de texto da indústria tipográfica e de impressos, e vem sendo utilizado desde o século XVI, quando um impressor desconhecido pegou uma bandeja de tipos e os embaralhou para fazer um livro de modelos de tipos. Lorem Ipsum sobreviveu não só a cinco séculos, como também ao salto para a editoração eletrônica, permanecendo essencialmente inalterado. Se popularizou na década de 60, quando a Letraset lançou decalques contendo passagens de Lorem Ipsum, e mais recentemente quando passou a ser integrado a softwares de editoração eletrônica como Aldus PageMaker. ",
      title: "Primeira aba"
    },
    {
      id: 1,
      content: "Neque porro quisquam est qui dolorem ipsum quia dolor sit amet, consectetur, adipisci velit...",
      title: "Segunda aba"
    },
    {
      id: 2,
      content: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam gravida orci massa, ut convallis arcu eleifend id. Sed turpis nisi, gravida at cursus eget, commodo in velit. Phasellus sit amet dapibus neque. Mauris rhoncus sem eu erat accumsan, a suscipit diam lobortis. Pellentesque ullamcorper feugiat diam malesuada mattis. Cras quis bibendum mi. Donec arcu tellus, suscipit quis suscipit sit amet, interdum rhoncus purus.",
      title: "Terceira aba"
    },])

</script>

<style scoped>
.tabs{
    display: flex;
    flex-wrap: nowrap;
    padding-left: 10px;
    justify-content: space-evenly;
}
.content{
    align-items: center;
    padding-left: 10px;
}
</style>