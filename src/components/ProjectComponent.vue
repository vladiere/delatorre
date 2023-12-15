<template>
  <div :class="Platform.is.mobile ? 'column bg-dark text-grey-2 q-pa-md' : 'column bg-dark text-grey-2'">

    <span :class="Platform.is.mobile ? 'q-my-lg text-weight-bolder text-accent text-h2 q-my-xl' : 'self-center text-h1 text-weight-bolder text-accent q-my-xl'">Projects</span>

    <div :class="Platform.is.mobile ? 'column q-gutter-y-md' : 'row'">
      <div :class="Platform.is.mobile ? 'column q-gutter-y-md' : 'col column q-px-xl q-gutter-y-md'">
        <span class="text-h4 text-weight-bold">Todo List App</span>
        <q-input v-model="newList" @keyup.enter="addNewList" class="bg-accent text-dark rounded-borders" standout="bg-accent text-white" label-color="dark" color="white" label="Add new list" dense >
          <template v-slot:after>
            <q-icon name="mdi-send" class="q-mr-sm" @click="addNewList" />
          </template>
        </q-input>
        <q-list bordered separator v-if="lists.length !== 0">
          <q-virtual-scroll
            :items="lists"
            v-slot="{ item, index }"
            style="max-height: calc(100vh - 350px)"
          >
            <q-item v-ripple :key="index" class="bg-accent text-dark">
              <q-item-section>
                <q-item-label :class="item.status === 'done' ? 'text-capitalize text-strike text-italic text-grey-7' : 'text-capitalize'">{{ item.todo }}</q-item-label>
              </q-item-section>
              <q-item-section side>
                <div class="row q-gutter-x-md">
                  <q-icon name="mdi-check-all" color="positive" class="cursor-pointer col" size="2em" @click="item.status === 'not' ? item.status = 'done' : item.status = 'not'"/>
                  <q-icon name="mdi-trash-can" color="negative" class="cursor-pointer col" size="2em" @click="lists.splice(index,1)"/>
                </div>
              </q-item-section>
            </q-item>
          </q-virtual-scroll>
        </q-list>
      </div>

      <div :class="Platform.is.mobile ? 'column q-gutter-y-md' : 'col column q-px-xl q-gutter-y-md'">
        <span class="text-h4 text-weight-bold">QR Code Generator</span>
        <q-input v-model="text" class="bg-accent rounded-borders" outlined dense color="grey-10" label="Text to encode"
          :rule="[
            val => (val && val.length > 0) || 'Cannot be empty'
          ]"
        />
        <q-btn @click="generateQRCode" color="accent" label="Generate QR Code" />
        <div class="column items-center">
          <canvas id="qr-code"></canvas>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { Platform, uid } from 'quasar';
import QRious from 'qrious';

const newList = ref('');
const lists = ref([]);

const addNewList = () => {
  if (newList.value) {
    lists.value.push({
      id: uid(),
      todo: newList.value,
      status: 'not',
    });

    newList.value = '';
  }
}

const text = ref('');
const qrCode = ref('');

const generateQRCode = () => {
  if (text.value != "" && text.value != "\n") {
    new QRious({
      level: "H",
      padding: 25,
      size: 300,
      element: document.getElementById("qr-code"),
      value: text.value,
    });
  }
};
</script>
