<template>
    <div class="page2">
        <p>This is page 2 Root content</p>
        <address-form />
    </div>
</template>

<script>

    import AddressForm from 'vue-address-form-v1-mf-structure'

    export default {
        name: "root",
        components:{
            AddressForm
        },
        data() {
            return {
                device: null
            }
        },
    }
</script>

<style>
</style>
