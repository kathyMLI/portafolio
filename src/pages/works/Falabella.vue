<template>
    <div>
    <q-page
    id="portada"
    ref="portada"
    class="box-1"
  >
    <div
     style="margin-top: -2%;"
     v-intersection="onIntersectionIndex"/>
    <PortadaContenido
    v-bind:marginTop="marginTop"
    v-bind:marginLeft="marginLeft"
    v-bind:subtitle="subtitle"
    v-bind:toptext="toptext"
    v-bind:subtext="subtext"
    v-bind:marginLeftTxt="marginLeftTxt"
    v-bind:urlPicture="'/'"
    v-bind:id="'-2'"
    v-bind:title="title"
    />
    </q-page>
    <q-page
    id="about"
    ref="about"
    style="min-height: 0%;"
    class="box-3"
  >
    <TextFolder
    v-bind:marginTop="marginTop"
    v-bind:marginLeft="marginLeft"
    v-bind:subtitle="'The Solution'"
    v-bind:toptext="toptext"
    v-bind:subtext="subtext"
    v-bind:marginLeftTxt="marginLeftTxt"
    v-bind:urlPicture="'/'"
    v-bind:id="5"
    v-bind:title="title"
    />
    </q-page>
    </div>
</template>
<script>
import PortadaContenido from './PortadaContenido.vue';
import TextFolder from './TextFolder.vue';

export default {
  name: 'Falabella',
  components: {
    PortadaContenido,
    TextFolder,
  },
  data() {
    return {
      position: 150,
      visibleIndex: true,
      visibleAbout: false,
      visibleWork: false,
      selected: 't_1',
      marginTop: '2%',
      marginLeft: '20%',
      marginLeftTxt: '50.6vw',
      title: 'Falabella',
      toptext: 'katherine.lib.ira@gmail.com',
      subtitle: 'The Brief',
      subtitleRight: 'The Solution',
      textParrafo: ' Geosort project, software responsible for planning, tracking and geocoding orders from Falabella.com.',
      tecnologias: ['Vue', 'Google Maps API', 'vue-chartjs'],
      subtext: 'I designed and developed a web interface using VUE from scratch with a maintainable, scalable and responsive code',
    };
  },
  methods: {
    onIntersectionIndex(entry) {
      this.visibleIndex = entry.isIntersecting;
    },
    onIntersectionAbout(entry) {
      this.visibleAbout = entry.isIntersecting;
    },
    onIntersectionWork(entry) {
      this.visibleWork = entry.isIntersecting;
    },
  },
};
</script>
