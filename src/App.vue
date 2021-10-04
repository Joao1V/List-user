<template>
  <AppDados @close="close" :show="show"></AppDados>
  <div>
    <h1 class="text-5xl text-white text-center mt-10">List User</h1>
    <div>
      <button
        class="
          flex
          border-2
          bg-gray-600
          border-black
          font-bold
          text-white
          hover:bg-black
          p-6
          rounded-md
          m-auto
          mt-10
          mb-10
        "
        @click="open"
      >
        Novo Registro
      </button>
    </div>
    <table
      class="table-fixed border border-collapse border-black mx-auto w-1/2"
    >
      <thead class="bg-gray-700 text-white">
        <th class="px-3 py-4">Nome</th>
        <th class="px-3 py-4">Telefone</th>
        <th class="px-3 py-4">Email</th>
        <th class="px-3 py-4">Ações</th>
      </thead>

      <tbody>
        <tr class="bg-white text-lg text-center">
          <td class="px-3 py-3 border border-black">nome</td>

          <td class="px-3 py-3 border border-black">telefone</td>

          <td class="px-3 py-3 border border-black">email</td>

          <td class="px-3 py-3 border border-black">
            <AppTrash class="px-3"></AppTrash>
            <AppEdit class="px-3"></AppEdit>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
import AppDados from "./components/AppDados.vue";
import AppTrash from "./components/AppTrash.vue";
import AppEdit from "./components/AppEdit.vue";
</script>

<script>
export default {
  data() {
    return {
      show: false,
    };
  },
  methods: {
    open() {
      this.show = true;
      console.log("chamou open");
    },
    close() {
      this.show = false;
      console.log("chamou close");
    },
  },
};
</script>