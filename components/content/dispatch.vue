<template>

<!--  <pre>{{ props }}</pre>-->
  <div v-if="props.type === 'button'" class="inline mr-1">
    <elements-button :style="2" :to="props.data.link" :download="props.data.download" >
      {{ props.data.label}}
    </elements-button>
  </div>

  <div v-else-if="props.type === 'person'" class="grid grid-cols-1 sm:grid-cols-2 xl:grid-cols-4 gap-8 p-0 pmcp-teacher_container">
    <ContentQuery v-for="t in props.data.teacher" :path="`teachers/${t}.nl`" find="one" v-slot="{ data }" >
      <elements-teacher :data="data" class="pmcp-teacher_element"/>
    </ContentQuery>


  </div>

</template>
<script setup>
const props = defineProps({
  data: Object,
  type: String
});
</script>
