<template>
    <Layout>
        <template v-slot:header>
            <Header v-bind:cv="cv"></Header>
        </template>

        <template v-slot:default>
            <Bio v-bind:cv="cv"></Bio>
        </template>
    </Layout>
</template>

<script>
import Layout from '@/containers/Layout.vue';
import Header from '@/containers/Header.vue';
import Bio from '@/containers/Bio.vue';

export default {
    name: 'App',
    components: {
        Layout,
        Header,
        Bio,
    },
    data() {
        return {
            cv: null,
        };
    },
    mounted() {
        fetch('data.json')
            .then(data => data.json())
            .then(data => {
                this.cv = data;
            });
    },
};
</script>

<style lang="scss">
:root {
    --accent: #079992;
    --accent-70: rgba(7, 153, 146, 0.7);
    --background: #454545;

    --text: #fff;
    --text-muted: rgba(255, 255, 255, 0.75);
    --bio-text: #fff;

    @media (prefers-color-scheme: light) {
        --background: #e9e9e9;

        --text: #555555;
        --text-muted: #606060;
        --bio-text: #e9e9e9;
    }

    @media print and (prefers-color-scheme: light) {
        --background: #fff;
        --bio-text: #fff;
    }
}

#app {
    min-height: 100%;
    height: 100%;
    min-width: 100%;
    width: 100%;
}

@import 'src/styles/base';
@import 'src/styles/print';
</style>
