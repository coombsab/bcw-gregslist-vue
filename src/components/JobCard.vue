<template>
    <div class="card">
      <div class="card-header d-flex justify-content-between align-items-center">
        <p class="m-0">{{job.jobTitle}}</p>
        <div class="align-items-center d-flex gap-2">
          <img :src="seller.picture" :alt="seller.name" :title="seller.name" height="30" class="rounded">
          <i class="mdi mdi-delete-forever fs-4 selectable rounded" @click="$emit('deleteClassified')"
            v-if="account.id == seller.id"></i>
        </div>
      </div>
      <router-link :to="{ name: 'Details', params:{ id: classifiedId }}">
        <div class="card-body d-flex justify-content-between align-items-center">
          <div>
            <h5><em>{{job.company}}</em></h5>
            <h5>{{job.hours}} hours / week</h5>
            <h4>${{job.rate}} / hour</h4>
            <p>{{job.description}}</p>
          </div>
        </div>
      </router-link>
    </div>
</template>

<script>
import { computed } from "@vue/reactivity";
import { AppState } from "../AppState.js";
import { Job } from "../models/Job.js";
import { SellerProfile } from "../models/SellerProfile.js";

export default {
  props: {
    job: { type: Job, required: true },
    seller: { type: SellerProfile, required: true },
    classifiedId: { type: String }
  },
  setup(props) {
    return {
      account: computed(() => AppState.account)
    }
  }
}
</script>

<style scoped lang="scss">
  
</style>