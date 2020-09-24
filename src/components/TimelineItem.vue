<template>
    <li class="dated-item" :class="{ subitem: isSubitem }">
        <span v-if="from != to" :class="!isSubitem ? 'h5' : 'h6'"
            >{{ from }} - {{ to }}</span
        >
        <span v-else :class="!isSubitem ? 'h5' : 'h6'">{{ from }}</span>
        <div>
            <h5 v-if="!isSubitem">{{ title }}</h5>
            <h6 v-else>{{ title }}</h6>
            <span v-if="text" class="subtext">
                {{ text }}
            </span>
        </div>
        <slot></slot>
    </li>
</template>

<script>
export default {
    name: 'TimelineItem',
    props: ['from', 'to', 'title', 'text', 'isSubitem'],
};
</script>

<style scoped lang="scss">
@import '@/styles/_variables.scss';

li {
    padding: 0;
    margin: 0;
    position: relative;
    margin-bottom: 0;
    padding-bottom: 0.5rem;
    &:after {
        content: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' height='20' width='20'%3E%3Ccircle cx='10' cy='10' r='10' fill='%23079992' /%3E%3C/svg%3E");
        position: absolute;
        left: -20px;
        top: 2px;
    }
    &:before {
        content: '';
        position: absolute;
        left: -12px;
        border-left: 4px solid var(--accent);
        height: 100%;
        width: 1px;
    }
    &:first-child {
        &:before {
            top: 6px;
        }
    }
    &:last-child {
        margin-bottom: 0;
        padding-bottom: 0;
        &:before {
            height: 6px;
        }
    }
}
li.subitem {
    padding-bottom: 0.3rem;
    &:after {
        content: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' height='20' width='20'%3E%3Ccircle cx='10' cy='10' r='7' fill='%23079992' /%3E%3Ccircle cx='10' cy='10' r='3' fill='%23454545' /%3E%3C/svg%3E");

        @media (prefers-color-scheme: light) {
            content: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' height='20' width='20'%3E%3Ccircle cx='10' cy='10' r='7' fill='%23079992' /%3E%3Ccircle cx='10' cy='10' r='3' fill='%23fff' /%3E%3C/svg%3E");
        }
    }
}

.dated-item {
    display: flex;

    > * {
        &:first-child {
            width: 8rem;
            text-align: center;
            margin-left: 0.5rem;
            margin-right: 0.5rem;
            color: var(--accent);
        }
        &:nth-child(2) {
            flex: 1;
        }
    }

    @media screen and (max-width: $s-break) {
        flex-direction: column;

        > * {
            &:first-child {
                text-align: left;
                margin-left: 1rem;
            }
            &:nth-child(2) {
                flex: 1;
                margin-left: 1rem;
            }
        }
    }
}
.subitem {
    color: var(--text-muted);
    .subtext {
        font-size: 0.8rem;
        margin-bottom: 0.5rem;
        display: inline-block;
    }
}
.dated-item.subitem {
    > * {
        &:first-child {
            color: var(--accent-70);
        }
    }
}
.subtext {
    font-size: 0.9rem;
    margin-bottom: 0.5rem;
    display: inline-block;
    white-space: pre-line;
}
</style>
