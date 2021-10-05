<template>
  <v-app>
    <Header1/>
    <v-main>
      <v-container>
        <v-row>
          <v-col cols="9">
            <Form1/>
          </v-col>
          <v-col cols="3">
            <Contact/>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import Header1 from './components/Header1';
import Form1 from './components/Form1';
import Contact from './components/Contact';

export default {
  name: 'App',
  components: {
    Header1,
    Form1,
    Contact
  },
};
</script>
