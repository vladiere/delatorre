<template>
  <div class="window-height column justify-center bg-dark text-grey-2 q-gutter-y-xl">

    <span class="q-ml-xl text-h3 text-weight-bolder text-grey-2">My Skills</span>

    <div class="row justify-center q-gutter-lg q-pa-lg">
      <div class="col-5 column q-gutter-y-sm">
        <span class="text-h5 text-accent text-weight-bold">TypeScript</span>
        <q-linear-progress rounded size="15px" :value="0.58" track-color="grey-1" color="accent" class="q-mt-sm" />
      </div>
      <div class="col-5 column q-gutter-y-sm">
        <div class="row justify-between">
          <span class="text-h5 text-accent text-weight-bold">JavaScript</span>
          <span class="text-h5 text-accent text-weight-bold">78%</span>
        </div>
        <q-linear-progress rounded size="15px" :value="0.78" track-color="grey-1" color="accent" class="q-mt-sm" />
      </div>
      <div class="col-5 column q-gutter-y-sm">
        <div class="row justify-between">
          <span class="text-h5 text-accent text-weight-bold">HTML-5</span>
          <span class="text-h5 text-accent text-weight-bold">88%</span>
        </div>
        <q-linear-progress rounded size="15px" :value="0.88" track-color="grey-1" color="accent" class="q-mt-sm" />
      </div>
      <div class="col-5 column q-gutter-y-sm">
        <div class="row justify-between">
          <span class="text-h5 text-accent text-weight-bold">CSS3</span>
          <span class="text-h5 text-accent text-weight-bold">67%</span>
        </div>
        <q-linear-progress rounded size="15px" :value="0.67" track-color="grey-1" color="accent" class="q-mt-sm" />
      </div>
      <div class="col-5 column q-gutter-y-sm">
        <div class="row justify-between">
          <span class="text-h5 text-accent text-weight-bold">VUEjs</span>
          <span class="text-h5 text-accent text-weight-bold">88%</span>
        </div>
        <q-linear-progress rounded size="15px" :value="0.88" track-color="grey-1" color="accent" class="q-mt-sm" />
      </div>
    </div>

    <q-btn outline color="accent" label="Contact" no-caps class="q-ml-xl self-start" size="xl" @click="scrollToComponent"/>
  </div>
</template>

<script setup>

const emits = defineEmits(['wantAScroll']);

const scrollToComponent = () => {
  emits('wantAScroll')
}
</script>
