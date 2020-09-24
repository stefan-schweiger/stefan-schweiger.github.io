<template>
<ul class="timeline">
    <slot></slot>
</ul>
</template>

<script>
export default {
    name: 'Timeline',
    props: ['cv'],
};
</script>

<style scoped lang="scss">
ul.timeline {
    list-style-type: none;
    padding: 0;
    margin-left: 20px;
}
</style>
