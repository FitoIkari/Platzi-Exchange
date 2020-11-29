<template>
  <div>
    <div>
      <bounce-loader :loading="isLoading" :color="'#68d391'" :size="100" />
    </div>
    <px-asset-table v-if="isLoading === false" :assets="assets" />
  </div>
</template>
<script>
import PxAssetTable from '@/components/PxAssetTable.vue';
import api from '@/api';

export default {
  components: { PxAssetTable },
  name: 'Home',

  data() {
    return {
      assets: [],
      isLoading: false
    };
  },

  created() {
    this.isLoading = true;
    api
      .getAssets()
      .then(assets => (this.assets = assets))
      .finally(() => (this.isLoading = false));
  }
};
</script>
