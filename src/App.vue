<script setup>
import { ref } from "vue";
import contacts from "./contacts.json";
const actors = ref([]);

// const addRandomContact = () => {
//       const remainingContacts = contacts.filter(contact => !actors.value.includes(contact));
//       const randomContact = remainingContacts[Math.floor(Math.random() * remainingContacts.length)];
//       ators.vcalue.push(randomContact);
//     };
const addRandomContact = () => {
  const remainingContacts = contacts.filter(contact => !actors.value.includes(contact));
  const randomIndex = Math.floor(Math.random() * remainingContacts.length);
  const randomContact = remainingContacts[randomIndex];
  actors.value.push(randomContact);
};
</script>

<template>
  <div>
    <h1 class="title">Iron Contacts</h1>
    <button @click="addRandomContact()">Add random contact</button>
    <table>
      <thead>
        <tr class="table-head-container">
          <th>Picture</th>
          <th>Name</th>
          <th>Popularity</th>
          <th>Won Oscar</th>
          <th>Won Emmy</th>
        </tr>
      </thead>
      <tbody>
        <tr class="table-data" v-for="(actor, index) in contacts.slice(0, 5)" :key="index">
          <td><img :src="actor.pictureUrl" :alt="actor.name" width="100"></td>
          <td>{{ actor.name }}</td>
          <td>{{ actor.popularity }}</td>
          <td>{{ actor.wonOscar ? 'Yes' : 'No' }}</td>
          <td>{{ actor.wonEmmy ? 'Yes' : 'No' }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style>
.title{
  text-align: center;
}
.table-head-container{
  display: flex;

}
table{
 width: 100%;
}
tr{
  display: flex;
  justify-content: space-between;
}
.table-data{
  margin-right: 30px;
  margin-top: 30px;
}
</style>
