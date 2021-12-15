<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>Blank</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Blank</ion-title>
        </ion-toolbar>
      </ion-header>

      <div id="container">
        <ion-button @click="openIonicModal">Ionic Modal</ion-button>
        <ion-button @click="openSimpleModal">Simple Modal</ion-button>
        <ion-button @click="openEmptyModal">Empty Modal</ion-button>
      </div>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar, IonButton, modalController } from '@ionic/vue';
import { defineComponent } from 'vue';
import EmptyModalVue from './EmptyModal.vue';
import IonicModalVue from './IonicModal.vue';
import SimpleModalVue from './SimpleModal.vue';

export default defineComponent({
  name: 'Home',
  components: {
    IonContent, IonHeader, IonPage, IonTitle, IonToolbar, IonButton
  }, setup() {

    async function openModal(modalComponent: any, cssClass?: string, props?: any, backdropDismiss = true) {
     
      cssClass = cssClass ? cssClass : '';
      props = props ? props : {};
      return modalController
        .create({
          component: modalComponent,
          cssClass: cssClass,
          componentProps: props,
          animated: false,
          backdropDismiss
        });
    }

    async function openIonicModal() {
      // It renders a modal with 27 Ion components (180ms)
      console.time("openIonicModal");
      const modal = await openModal(IonicModalVue);
      await modal.present();
      console.timeEnd("openIonicModal");
    }

    async function openSimpleModal() {
      // It renders a modal with 350 divs (150ms)
      console.time("openSimpleModal");
      const modal = await openModal(SimpleModalVue);
      await modal.present();
      console.timeEnd("openSimpleModal");
    }

    async function openEmptyModal() {
      // It renders a modal with 1 div (30ms)
      console.time("openEmptyModal");
      const modal = await openModal(EmptyModalVue);
      await modal.present();
      console.timeEnd("openEmptyModal");
    }

    return {
      openIonicModal,
      openSimpleModal,
      openEmptyModal
    };
  }
});
</script>

<style scoped>
#container {
  text-align: center;
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}
</style>