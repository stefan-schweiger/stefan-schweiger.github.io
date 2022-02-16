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
    --primary: #89cba0;
    --primary-contrast: #333f4c;
    --primary-70: rgb(137 203 160 / 0.7);
    --background: #333f4c;

    --text: #fff;
    --text-muted: rgb(255 255 255 / 0.75);

    @media (prefers-color-scheme: light) {
        --primary: #71b789;
        --primary-contrast: #fff;
        --primary-70: rgb(113 183 137 / 0.7);
        --background: #e9e9e9;

        --text: #333f4c;
        --text-muted: rgb(51 63 77 / 0.75);
    }

    @media print and (prefers-color-scheme: light) {
        --background: #fff;
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
