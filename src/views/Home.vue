<template>
    <div>
        <bounce-loader :loading="isLoading" :color="'#68d391'" :size="100"></bounce-loader>
        <px-assets-table v-if="!isLoading" :assets="assets"/>
    </div>
</template>

<script>
import api from '@/api.js'
import PxAssetsTable from "@/components/PxAssetsTable.vue";
export default {
    name: 'MyHome',
    components: {
        PxAssetsTable
    },
    data(){
        return {
            assets: [],
            isLoading: false
        }
    },
    created(){
        this.isLoading = true;
        api.getAssets()
        .then( data => this.assets = data)
        .finally(() => this.isLoading = false );
    }
}
</script>
