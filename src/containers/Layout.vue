<template>
    <div class="grid-container">
        <header>
            <slot name="header"></slot>
        </header>
        <main>
            <slot></slot>
        </main>
    </div>
</template>

<script>
export default {
    name: 'Layout',
};
</script>

<style scoped lang="scss">
@import '@/styles/_variables';

.grid-container {
    display: grid;
    grid-template-columns: 1fr 1.618fr;
    grid-template-rows: 1fr;
    gap: 0px 0px;
    grid-template-areas: "header bio";
    height: 100%;
    width: 100%;

    @media screen and (max-width: $l-break) {
        display: grid;
        grid-template-columns: 1fr;
        grid-template-rows: auto 1fr;
        grid-template-areas: "header" "bio";
    }
}

header {
    color: var(--bio-text);
    grid-area: header;
    background-color: var(--accent);
    display: flex;
    flex: 1;
    flex-direction: column;
    align-content: flex-end;
    align-items: flex-end;
    position: relative;

    & > * {
        height: 100vh;
        flex-direction: column;
        display: flex;
        flex: 1;
        align-content: flex-end;
        align-items: flex-end;
        justify-content: center;
        margin-right: 2rem;

        @media screen and (max-width: $l-break) {
            flex-direction: row-reverse;
            height: auto;
            align-items: center;
            margin: 1.5rem 1rem;
        }
    }
}

main {
    grid-area: bio;
    background: var(--background);
    color: var(--text);
    padding-top: 3rem;
    padding-left: 3rem;
    padding-right: 3rem;
    font-weight: 300;
    overflow-y: auto;

    @media screen and (max-width: $l-break) {
        overflow-y: visible;
    }

    & > * {
        max-width: 50rem;
    }
}

.actions {
    position: absolute;
    left: 0;
    bottom: 0;
    margin: 0.4rem;

    @media print {
        display: none;
    }
}
</style>
