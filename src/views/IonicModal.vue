<template>
  <ion-content>
    <template v-for="(value, index) of [1, 2, 3, 4, 5, 6]" :key="index">
      <ion-row class="ion-text-center">
        <ion-col class="ion-no-padding ion-text-center" size="3" v-for="(value2, index2) of [1, 2, 3, 4]" :key="index2">
          <ion-card class="modifier">
            <ion-row class="ion-no-padding ion-text-center">
              <ion-col size="4" class="ion-text-center">
                {{ value2 }}
              </ion-col>
              <ion-col size="4" class="ion-text-center">
                {{ value2 }}
              </ion-col>
              <ion-col size="4" class="ion-text-center">
                {{ value2 }}
              </ion-col>
            </ion-row>
          </ion-card>
        </ion-col>
      </ion-row>
    </template>
  </ion-content>
</template>

<script lang="ts">
import { IonCol, IonRow, IonCard, IonContent } from '@ionic/vue';
import { defineComponent } from 'vue';
export default defineComponent({
  name: 'IonicModal',
  components: {
    IonContent, IonCard, IonRow, IonCol
  }, setup() {
    return {
    };
  }
});
</script>

<style scoped>
</style>