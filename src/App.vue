<template>
  <q-layout id="q-app" ref="app" view="hHh lpR fFf">
    <q-header
    :class="visibleClass"
    text-positive
    height-hint="98">
      <q-toolbar>
        <q-toolbar-title>
          <router-link
            to="/"
            class="text-white"
            style="text-decoration: none;">
            <q-avatar>
            </q-avatar>
          </router-link>
        </q-toolbar-title>
        <q-tabs
        v-model="selected" align="center"
        horizontal>
        <q-tab name="me" v-on:click="scrollToPortada" label="Me"/>
        <!-- <q-tab name="about" v-on:click="scrollToAbout" label="About"/> -->
        <q-tab name="work" v-on:click="scrollToWork" label="Work"/>
      </q-tabs>
      </q-toolbar>
    </q-header>
    <q-footer>
        <q-toolbar>
          <q-toolbar-title
          v-on:click="openURL(urlGmail)"
          style="cursor: pointer; display: flex;color: rgb(39, 52, 96);justify-content: center;">
            Have something cool to share?
            Pop me a message!
            katherine.lib.ira@gmail.com
          </q-toolbar-title>
        </q-toolbar>
      </q-footer>

    <q-page-container>
      <transition name="fade">
        <router-view />
      </transition>
    </q-page-container>
  </q-layout>
</template>
<script>
import { openURL } from 'quasar';
import EventBus from './event-bus';

export default {
  name: 'App',
  data() {
    return {
      position: 150,
      visibleIndex: true,
      visibleAbout: false,
      visibleWork: false,
      selected: 't_1',
      urlGmail: 'https://mail.google.com/mail/?view=cm&fs=1&to=katherine.lib.ira@gmail.com&su=I%20have%20a%20project%20in%20mind&body=I%20hope%20hear%20from%20you%20soon!',
      visibleClass: 'bg-accent text-white transition',
    };
  },
  mounted() {
    EventBus.$on('selectedValue', (payload) => {
    // handle event
      console.log('selectedValue: ', payload);
      this.selected = payload;
    });
    EventBus.$on('classValue', (payload) => {
    // handle event
      console.log('classValue: ', payload);
      this.visibleClass = payload;
    });
  },
  methods: {
    openURL,
    scrollToPortada() {
      this.$router.push('/#portada').then(() => window.scrollTo({ top: 0, behavior: 'smooth' }));
      /* const el = this.$refs.app.$el;
      // MUST call it in timer
      setTimeout(() => {
        el.scrollIntoView({ block: 'start', behavior: 'smooth' });
        // window.scrollTo({ top: 500, behavior: 'smooth' });
      }, 100); */
    },
    onIntersectionIndex(entry) {
      this.visibleIndex = entry.isIntersecting;
    },
    onIntersectionAbout(entry) {
      this.visibleAbout = entry.isIntersecting;
    },
    onIntersectionWork(entry) {
      this.visibleWork = entry.isIntersecting;
    },
    scrollToAbout() {
      this.$router.push('/#about');
    },
    scrollToWork() {
      this.$router.push('/#work');
    },
  },
};
</script>
