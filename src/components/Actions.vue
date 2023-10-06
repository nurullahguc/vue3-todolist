<script setup>

const props = defineProps({
    id: Number,
})

</script>


<template>
    <button class="btn btn-warning mr-1" :data-id="props.id">Edit</button>
    <button class="btn btn-danger mr-1" :data-id="props.id">Delete</button>
    <button class="btn btn-info mr-1" :data-id="props.id">Change Status</button>
</template>