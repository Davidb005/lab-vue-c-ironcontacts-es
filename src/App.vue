<script setup>
import { ref, watch } from "vue";
import allContacts from "./contacts.json";
const contacts = ref([]);

const addRandomContact = () => {
  const remainingContacts = allContacts.filter(contact => !contacts.value.includes(contact));
  const randomIndex = Math.floor(Math.random() * remainingContacts.length);
  const randomContact = remainingContacts[randomIndex];
  contacts.value.push(randomContact);
};

const sortElementsByName = () => {
  contacts.value.sort((a, b) => a.name.localeCompare(b.name));
};

const sortElementsByPopularity = () => {
  contacts.value.sort((a, b) => b.popularity - a.popularity);
};

const removeContact = (index) => {
  contacts.value.splice(index, 1);
};
</script>

<template>
  <div>
    <h1 class="title">Iron Contacts</h1>
    <div class="button-container">
    <button class="button" @click="addRandomContact">Add random contact</button>
    <button class="button"  @click="sortElementsByName">Sort by name</button>
    <button class="button" @click="sortElementsByPopularity">Sort by popularity</button>
    </div>
    <table>
      <thead>
        <tr class="table-head-container">
          <th class="picture">Picture</th>
          <th>Name</th>
          <th>Popularity</th>
          <th>Won Oscar</th>
          <th>Won Emmy</th>
        </tr>
      </thead>
      <tbody>
        <tr class="table-data" v-for="(actor, index) in contacts" :key="index">
          <td><img :src="actor.pictureUrl" :alt="actor.name" width="100" /></td>
          <td>{{ actor.name }}</td>
          <td>{{ actor.popularity }}</td>
          <td>{{ actor.wonOscar ? "Yes" : "No" }}</td>
          <td>{{ actor.wonEmmy ? "Yes" : "No" }}</td>
          <button @click="removeContact" class="remove-button">Delete</button>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style>
.title {
  text-align: center;
}
.table-head-container {
  display: flex;
  justify-content: space-evenly;
  margin-right: 120px;
}
table {
  width: 100%;
}
tr {
  display: flex;
  justify-content: space-between;
}
.table-data {
  margin-right: 30px;
  margin-top: 30px;
}
.button-container{
  display: flex;
  justify-content: space-around;
  border: 10px, solid, black;
  
}
.button{
  background-color: black;
  color: white;
  margin-bottom: 60px;
  margin-top: 40px;
  
}
.button:hover{
  cursor: pointer;
  color:blue
}
.picture{
  align-content: flex-start;
  margin-left: 0;
}
</style>
