<template>
  <div>
    <v-form v-model="valid" ref="form" lazy-validation>
            <v-text-field
          label="Name"
          v-model="name"
          :rules="nameRules"
          :counter="10"
          required
        ></v-text-field>
        <v-text-field
          label="E-mail"
          v-model="email"
          :rules="emailRules"
          required
        ></v-text-field>
        <v-select
          label="Item"
          v-model="select"
          :items="items"
          :rules="[v => !!v || 'Item is required']"
          required
        ></v-select>
        <v-btn
          @click="submit"
          :disabled="!valid"
        > submit </v-btn>
        <v-btn @click="clear">clear</v-btn>
    </v-form>
  </div>
</template>

<script>
export default {
  name: 'tabs',
  data: () => ({
    valid: true,
    name: '',
    nameRules: [
      v => !!v || 'Name is required',
      v => (v && v.length <= 10) || 'Name must be less than 10 characters'
    ],
    email: '',
    emailRules: [
      v => !!v || 'E-mail is required',
      v => /^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/.test(v) || 'E-mail must be valid'
    ],
    select: null,
    items: [
      'Item 1',
      'Item 2',
      'Item 3',
      'Item 4'
    ],
    checkbox: false
  })
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
div{
  width: 50%;
  margin: auto;
  font-family: sans-serif;
}
</style>
