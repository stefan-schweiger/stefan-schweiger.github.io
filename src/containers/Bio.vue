<template>
    <div>
        <h3 class="d-print-none">About me</h3>
        <p class="d-print-none about-me">
            {{ cv?.about }}
        </p>

        <h3>Education</h3>
        <Timeline>
            <TimelineItem
                v-for="item in cv?.education"
                :key="item.id"
                :from="item.from"
                :to="item.to"
                :title="`${item.school} - ${item.field}`"
                :text="item.details"
            ></TimelineItem>
        </Timeline>

        <h3>Work</h3>
        <Timeline>
            <template v-for="item in cv?.work" :key="item.id">
                <TimelineItem
                    :from="item.from"
                    :to="item.to"
                    :title="`${item.company} - ${item.role}`"
                    :text="item.details"
                ></TimelineItem>

                <TimelineItem
                    v-for="project in item.projects"
                    :key="project.id"
                    :from="project.from"
                    :to="project.to"
                    :title="project.name"
                    :text="project.details"
                    :is-subitem="true"
                ></TimelineItem>
            </template>
        </Timeline>

        <h3>Skills</h3>
        <div class="skill-container-grid">
            <SkillSet
                v-for="skillSet in cv?.skillSets"
                :key="skillSet.id"
                :category="skillSet.category"
            >
                <Skill
                    v-for="skill in skillSet.skills"
                    :key="skill.id"
                    :name="skill.name"
                    :rating="skill.rating"
                ></Skill>
            </SkillSet>
        </div>
    </div>
</template>

<script>
import Timeline from '@/components/Timeline.vue';
import TimelineItem from '@/components/TimelineItem.vue';
import Skill from '@/components/Skill.vue';
import SkillSet from '@/components/SkillSet.vue';

export default {
    name: 'Bio',
    props: ['cv'],
    components: {
        Timeline,
        TimelineItem,
        Skill,
        SkillSet,
    },
};
</script>

<style scoped lang="scss">
@import '@/styles/_variables';

.about-me {
    white-space: pre-line;
}

.skill-container-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    column-gap: 3rem;

    @media screen and (max-width: $m-break) {
        grid-template-columns: 1fr;
    }

    @media screen and (min-width: ($l-break + 1px)) and (max-width: $xl-break) {
        column-gap: 1.5rem;
    }
}
</style>
