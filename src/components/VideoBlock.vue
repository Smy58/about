<template>
    <div class="vidblock" id="vidblock">
        <h2 class="vidblock__title">Как я работаю</h2>
        <p class="vidblock__text">Lorem Ipsum - это текст-"рыба", часто используемый в печати и вэб-дизайне. Lorem Ipsum является стандартной "рыбой" для текстов на латинице с начала XVI века.</p>

        <div class="vidblock__img"></div>
    </div>
</template>

<script>
export default {
    name: 'VideoBlock',
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
            let obj = document.querySelector('#vidblock');
            let {top} = obj.getBoundingClientRect();
            let height = document.documentElement.clientHeight;
            this.$emit('setScroll', (top < (height * 0.55) && top >= 0) ? 4 : 0 );
        }
    }
}
</script>

<style lang="sass">
.vidblock
    width: 100%
    padding-top: 100px
    padding-bottom: 100px

    display: flex
    flex-direction: column
    align-items: center

    &__title
        font-weight: 500
        font-size: 32px
        line-height: 38px
        text-align: center

        color: $black

        margin-bottom: 50px

    &__text
        width: 540px
        font-weight: 400
        font-size: 16px
        line-height: 26px
        text-align: center

        color: $grey
        margin-bottom: 57px

    &__img
        width: 1110px
        height: 600px

        background: url(@/assets/fake-video.png)
        background-repeat: no-repeat
        background-size: contain

@media screen and (max-width: 1250px)
    .vidblock
        padding-bottom: 50px
        padding-top: 50px
        &__img
            width: 70%
            height: 38vw

        &__text
            width: 55%
</style>