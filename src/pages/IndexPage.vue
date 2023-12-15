<template>
  <q-page class="column">
    <div class="window-height column justify-center q-gutter-y-md bg-dark q-pl-xl">
      <span class="text-h5 text-accent">Hello! I am</span>
      <span class="text-h1 text-grey-2 text-weight-bolder">John Patrick Delatorre</span>
      <div class="column">
        <span class="text-h5 text-weight-bolder text-accent">Front-end Developer</span>
        <div class="row q-gutter-x-md text-grey-2">
          <span class="text-h6 text-weight-regular">Front-end Developer</span>
          <div class="relative-position">
            <div class="bg-accent absolute-center" style="padding: 5px;border-radius:50%;"></div>
          </div>
          <span class="text-h6 text-weight-regular">Programmer</span>
        </div>
      </div>
      <q-btn outline color="accent" label="About me" no-caps class="self-start" size="xl" @click="scrollToComponent('about')"/>
    </div>

    <AboutComponent ref="aboutComponent" @wantAScroll="scrollToComponent('skill')" />
    <SkillComponent ref="skillComponent" @wantAScroll="scrollToComponent('contact')" />
    <ContactComponent ref="contactComponent" @wantAScroll="scrollToComponent('project')" />
    <ProjectComponent ref="projectComponent" />
  </q-page>
</template>

<script setup>
import { defineComponent, ref } from 'vue'
import AboutComponent from 'components/AboutComponent.vue';
import SkillComponent from 'components/SkillComponent.vue';
import ContactComponent from 'components/ContactComponent.vue';
import ProjectComponent from 'components/ProjectComponent.vue';

defineComponent({
  name: 'IndexPage'
});

const aboutComponent = ref(null);
const skillComponent = ref(null);
const contactComponent = ref(null);
const projectComponent = ref(null);

const scrollToComponent = (option) => {
  console.log(option)
  if (option === 'about') {
    aboutComponent.value.$el.scrollIntoView({
      behavior: 'smooth',
      block: 'start'
    })
  } else if (option === 'skill') {
    skillComponent.value.$el.scrollIntoView({
      behavior: 'smooth',
      block: 'start'
    })
  } else if (option === 'contact') {
    contactComponent.value.$el.scrollIntoView({
      behavior: 'smooth',
      block: 'start'
    })
  } else if (option === 'project') {
    projectComponent.value.$el.scrollIntoView({
      behavior: 'smooth',
      block: 'start'
    })
  }
}
</script>
