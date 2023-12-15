<style lang="sass" scoped>
.picture
  -webkit-filter: brightness(110%) contrast(110%) grayscale(100%)
  filter: brightness(110%) contrast(110%) grayscale(100%)
  transition: 500ms cubic-bezier(0.12, 0, 0.39, 0)

  &:hover
    -webkit-filter: contrast(90%) sepia(20%)
    filter: contrast(90%) sepia(20%)
</style>

<template>
  <div :class="Platform.is.mobile ? 'window-height column justify-center bg-dark text-grey-2' : 'window-height column justify-center bg-dark text-grey-2'">
    <div :class="Platform.is.mobile ? 'column reverse items-center q-pa-md' : 'row q-px-xl q-gutter-x-lg items-center'">
      <div class="col column q-gutter-y-md">
        <span :class="Platform.is.mobile ? 'text-center text-subtitle1 text-weight-light' : 'text-h6 text-weight-light'">
          Greetings! I'm John Patrick Delatorre, a devoted software engineer specializing in web, mobile, and desktop applications. My expertise centers around JavaScript, and I'm dedicated to making the web more accessible. I will earned my bachelor's degree in Information Technology in Cordova Public College. Eager to explore job opportunities aligned with my passion and skills.
        </span>
        <q-btn outline color="accent" label="Skills" no-caps class="self-start" size="xl" @click="scrollToComponent"/>
      </div>
      <div :class="Platform.is.mobile ? 'column ' : 'col column items-center'">
        <img class="picture rounded-borders" src="~assets/picture.png" />
      </div>
    </div>
  </div>
</template>

<script setup>
import { Platform } from 'quasar';

const emits = defineEmits(['wantAScroll']);

const scrollToComponent = () => {
  emits('wantAScroll')
}
</script>
