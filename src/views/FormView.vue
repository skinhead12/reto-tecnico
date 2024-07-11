<template>
  <div class="form-container">
    <FormData />
    <PopUp />
    <TableInfo />
  </div>
</template>

<script>
import FormData from "@/components/FormData.vue";
import PopUp from "@/components/PopUp.vue";
import TableInfo from "@/components/TableInfo.vue";

export default {
  name: "HomeView",
  components: {
    FormData,
    PopUp,
    TableInfo,
  },
};
</script>
