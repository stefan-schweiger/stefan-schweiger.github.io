<template>
    <span class="skill-name">{{ name }}</span>
    <svg class="rating" height="20" width="120" viewBox="0 0 120 20">
        <circle
            v-for="n in rating * 5"
            :key="n"
            :cx="10 + 25 * (n - 1)"
            cy="10"
            r="10"
            fill="#079992"
        />
        <circle
            v-for="n in 5"
            :key="n"
            :cx="10 + 25 * (n - 1)"
            cy="10"
            r="4"
            stroke="#079992"
            fill="transparent"
        />
    </svg>
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
}
</style>
