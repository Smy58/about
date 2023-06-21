<template>
    <section class="projects" id="projects">
        <div class="project project_1">
            <div class="project__hov"><div class="project__eye"></div></div>
        </div>
        <div class="project project_2">
            <div class="project__hov"><div class="project__eye"></div></div>

        </div>
        <div class="project project_3">
            <div class="project__hov"><div class="project__eye"></div></div>

        </div>
        <div class="project project_4">
            <div class="project__hov"><div class="project__eye"></div></div>
            \
        </div>
        <div class="project project_5">
            <div class="project__hov"><div class="project__eye"></div></div>

        </div>
        <div class="project project_6">
            <div class="project__hov"><div class="project__eye"></div></div>

        </div>
        <div class="project project_7">
            <div class="project__hov"><div class="project__eye"></div></div>

        </div>
        <div class="project project_8">
            <div class="project__hov"><div class="project__eye"></div></div>

        </div>
    </section>
</template>

<script>
export default {
    name: 'ProjectsBlock',
    props: {
        setScroll: Function
    },
    created() {
        window.addEventListener('scroll', this.handleScroll);
    },
    unmounted() {
        window.removeEventListener('scroll', this.handleScroll);
    },
    methods: {
        handleScroll() {
            let obj = document.querySelector('#projects');
            let {top} = obj.getBoundingClientRect();
            let height = document.documentElement.clientHeight;
            this.$emit('setScroll', (top < (height * 0.55) && top >= 0) ? 3 : 0 );
        }
    }
}
</script>

<style lang="sass">
.projects
    width: 100vw
    display: flex
    flex-direction: row
    flex-wrap: wrap
    justify-content: center
    align-items: center

.project
    width: 25vw
    height: 25vw

    border: 0.5px solid $dark-blue
    box-sizing: border-box

    background: url(@/assets/pr1.png)
    background-repeat: no-repeat
    background-size: contain

    position: relative

    &__hov
        width: 100%
        height: 100%
        position: absolute
        top: 0
        left: 0
        background: $blue-bg
        opacity: 0

        transition: opacity 0.5s ease

        display: flex
        align-items: center
        justify-content: center

        &:hover
            opacity: 0.5

    &__eye
        width: 33%
        height: 33%
        background: url(@/assets/eye.png)
        background-repeat: no-repeat
        background-size: contain

@media screen and (max-width: 770px)
    .projects
        width: 99vw

    .project
        width: 33vw
        height: 33vw
        &__hov
            width: 33vw
            height: 33vw

@media screen and (max-width: 600px)
    .projects
        width: 100vw

    .project
        width: 50vw
        height: 50vw
        &__hov
            width: 50vw
            height: 50vw
</style>