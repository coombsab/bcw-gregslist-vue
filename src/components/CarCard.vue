<template>
  <div class="card">
    <router-link :to="{ name: 'Details', params:{ id: classifiedId }}">
      <img class="rounded-top img-fluid" :src="car.imgUrl" :alt="car.make">
    </router-link>
    <div class="card-body d-flex justify-content-between align-items-center">
      <h5>{{car.make}} {{car.model}}</h5>
      <div class="align-items-center d-flex gap-2">
        <img :src="seller.picture" :alt="seller.name" :title="seller.name" height="30" class="rounded">
        <i class="mdi mdi-delete-forever fs-4 selectable rounded" @click="$emit('deleteClassified')"
          v-if="account.id == seller.id"></i>
      </div>
    </div>
  </div>
</template>


<script>
import { computed } from '@vue/reactivity';
import { onMounted } from 'vue';
import { AppState } from '../AppState.js';
import { Car } from '../models/Car.js';
import { SellerProfile } from '../models/SellerProfile.js';

export default {
  props: {
    car: { type: Car, required: true },
    seller: { type: SellerProfile, required: true },
    classifiedId: { type: String }
  },
  setup(props, { emit }) {

    onMounted(() => {
      // console.log('neat huh???')

    })

    return {
      account: computed(() => AppState.account),
      // classifiedId: computed(() => AppState.activeClassified.id),
      deleteClassified() {
        emit('deleteClassified')
      }
    }
  }
}
</script>


<style lang="scss" scoped>

</style>
