<template>
    <section class="about" id="about">
        <div class="about__info">
            <h2 class="about__title">Обо мне</h2>
            <p class="about__text">Lorem Ipsum - это текст-"рыба", часто используемый в печати и вэб-дизайне. Lorem Ipsum является стандартной "рыбой" для текстов на латинице с начала XVI века.</p>
        </div>
    </section>    
</template>

<script>
export default {
    name: 'AboutBlock',
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
            let obj = document.querySelector('#about');
            let {top} = obj.getBoundingClientRect();
            let height = document.documentElement.clientHeight;
            this.$emit('setScroll', (top < (height * 0.55) && top >=0) ? 2 : 0 );
        }
    }
}
</script>

<style lang="sass">
.about
    background: $white-bg
    width: 100%
    padding-top: 119px
    padding-bottom: 100px

    display: flex
    flex-direction: column
    align-items: center
    justify-content: center

    &__info
        width: 30%

    &__title
        font-weight: 500
        font-size: 32px
        line-height: 38px
        text-align: center
        color: $black

        margin-bottom: 50px

    &__text
        font-weight: 400
        font-size: 16px
        line-height: 26px
        text-align: center
        color: $grey

@media screen and (max-width: 700px)
    .about
        &__info
            width: 70%
</style>