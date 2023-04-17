<template>
    <section class="section-wrapper Skills">
        <h3 class="title1">How i can serve you</h3>
        <div class="skills-wrapper">
            <div class="skill" v-for="(skill, key) in skills" :key="skill.title">
<h4><span class="icon">I</span>{{ skill.title }}</h4>
<p>{{ skill.text }}</p>
            </div>
        </div>

    </section>
</template>

<script>
export default {
    data() {
        return {
        skills: [
            { title: 'Frontend development', text: 'Lorem ipsum dolor sit amet consectetur. Convallis ultrices nunc consectetur ipsum laoreet neque ut arcu. In duis ut varius pulvinar ornare aliquet dui quis con', icon: '', activeBg: true },
            { title: '', text: '', icon: '', activeBg: true },
            { title: '', text: '', icon: '', activeBg: true }
        ]
        }
    }
}
</script>