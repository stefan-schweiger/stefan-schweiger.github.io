<template>
    <span class="skill-name">{{ name }}</span>
</template>

<script>
export default {
    name: 'Skill',
    props: ['name', 'rating'],
};
</script>

<style scoped lang="scss">
.skill-name {
    text-align: right;
    margin-bottom: 0.3rem;
    padding: 0.25rem 0.75rem;
    border-radius: 1rem;
    background: var(--accent);
    color: white;
    font-size: 0.75rem;
}
</style>
