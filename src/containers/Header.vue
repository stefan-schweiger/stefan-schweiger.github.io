<template>
    <div>
        <img :src="cv?.picture" class="image rounded-circle" />
        <div class="header-details">
            <div class="name">
                {{ cv?.firstName }}
                <span style="font-weight: 500">{{
                    cv?.lastName.toUpperCase()
                }}</span>
                <span v-if="cv?.title">, {{ cv?.title }}</span>
            </div>
            <div class="position">
                {{ cv?.position }}
            </div>
            <div>
                <a :href="`mailto:${cv?.email}`">{{ cv?.email }}</a>
            </div>
            <div>
                <a :href="`tel:${cv?.phone.replace(/\s+/g, '')}`">{{
                    cv?.phone
                }}</a>
            </div>
            <div>{{ cv?.city }}, {{ cv?.country }}</div>

            <div class="about-me d-print-block d-none">
                <h3 class="m-0">About me</h3>
                <p>
                    {{ cv?.about }}
                </p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Header',
    props: ['cv'],
};
</script>

<style scoped lang="scss">
@import '@/styles/_variables';

.image {
    margin-top: 1rem;
    margin-bottom: 1rem;
    margin-left: 1.5rem;
    height: 200px;
    width: 200px;
    background: var(--background);
    border: 0.25rem solid var(--background);
    border-radius: 50%;

    @media screen and (max-width: $l-break) {
        height: 100px;
        width: 100px;
    }
}

.header-details {
    margin-right: 5px;
    font-weight: 300;
    text-align: right;
}

.name {
    font-size: 2rem;

    @media screen and (max-width: $l-break) {
        font-size: 1.8rem;
    }

    @media screen and (max-width: $s-break) {
        font-size: 1.3rem;
    }
}

.about-me {
    white-space: pre-line;
}
</style>
