<template>
  <v-data-table class="elevation-1">
    <template v-slot:default>
      <thead>
        <tr>
          <th class="text-left">Id</th>
          <th class="text-left">Name</th>
          <th class="text-left">Email</th>
          <th class="text-left">Website</th>
          <th class="text-left">Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="list in listData" :key="list.id">
          <td>{{ list.id }}</td>
          <td>{{ list.name }}</td>
          <td>{{ list.email }}</td>
          <td>{{ list.website }}</td>
          <td>
            <v-icon small class="mr-2"> mdi-pencil </v-icon>
            <v-icon small> mdi-delete </v-icon>
          </td>
        </tr>
      </tbody>
    </template>
  </v-data-table>
</template>

<script>
export default {
  data() {
    return {
      listData: [],
    };
  },
  mounted() {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then((result) => result.json())
      .then((result) => (this.listData = result));
  },
};
</script>
