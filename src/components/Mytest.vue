<script lang="ts" setup>
import { ref, inject } from 'vue'

interface LOC {
    location: string,
    updateLocation: any
}

const location = inject<LOC>('location')

const msg = ref('test component')

</script>
<template>
    <p>{{ msg }},{{ location?.location }}</p>
</template>