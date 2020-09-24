<template>
<div>
    <h5>{{ category }}</h5>
    <div class="skill-grid">
        <slot></slot>
    </div>
</div>
</template>

<script>
export default {
    name: 'Skill',
    props: ['category'],
};
</script>

<style scoped lang="scss">
@import '@/styles/_variables';

.skill-grid {
    display: grid;
    grid-template-columns: 1fr min-content;
    margin-left: 1.5rem;
    margin-bottom: 1.5rem;
    column-gap: 1.5rem;

    @media screen and (min-width: ($l-break + 1px)) and (max-width: $xl-break) {
        margin-left: 1rem;
    }
}
</style>
