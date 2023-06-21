<template>
    <section class="main" id="main">
        <div class="main__computer"></div>
        <div class="main__info">
            <h2 class="main__title">Дизайн и верстка</h2>
            <p class="main__text">Lorem Ipsum - это текст-"рыба", часто используемый в печати и вэб-дизайне. Lorem Ipsum является стандартной "рыбой" для текстов на латинице с начала XVI века.</p>
            <div class="main__button">написать мне</div>
        </div>
    </section>
</template>

<script>
export default {
    name: 'MainBlock',
    props: {
    },
    created() {
        window.addEventListener('scroll', this.handleScroll);
    },
    unmounted() {
        window.removeEventListener('scroll', this.handleScroll);
    },
    methods: {
        handleScroll() {
            // console.log('scroll ev')
            let obj = document.querySelector('#main');
            let {top} = obj.getBoundingClientRect();
            let height = document.documentElement.clientHeight;
            // console.log(top, (height * 0.55))
            this.$emit('setScroll', (top < (height * 0.55) && top >= 0) ? 1 : 0 );
        }
    }
}
</script>

<style lang="sass">
.main
    padding-top: 120px
    width: 1120px
    height: 540px
    display: flex
    flex-direction: row
    align-items: center
    justify-content: space-between

    &__computer
        width: 357px
        height: 233.7px
        background: url(@/assets/computer.png)
        background-repeat: no-repeat
        background-size: contain
    
    &__info
        display: flex
        flex-direction: column
        align-items: flex-start
        width: 541px

    &__title
        font-weight: 500
        font-size: 48px
        line-height: 79px

        color: $black
        margin-bottom: 60px

    &__text
        font-weight: 400
        font-size: 16px
        line-height: 26px

        color: $grey
        margin-bottom: 60px

    &__button
        width: 225px
        height: 65px
        background: $blue-button
        font-weight: 400
        font-size: 16px
        line-height: 26px
        text-align: center
        letter-spacing: 0.1em

        text-transform: uppercase

        display: flex
        align-items: center
        justify-content: center

        color: $button-text

@media screen and (max-width: 1250px) 
    .main
        width: 70%

        &__computer
            width: 21vw
            height: 14vw
        
        &__info
            width: 36vw

        &__title
            font-size: 3vw
            line-height: 4vw
            margin-bottom: 4vw
        &__text
            font-size: 1.4vw
            line-height: 2.1vw
            margin-bottom: 4vw
        &__button
            font-size: 1.4vw
            line-height: 2.1vw
            width: 18.4vw
            height: 5.3vw

@media screen and (max-width: 600px)
    .main
        width: 90%
        flex-direction: column

        height: auto
        padding-top: 50px
        padding-bottom: 50px


        &__computer
            width: 70vw
            height: 46vw
            margin-bottom: 40px

        &__info
            width: 80%

        &__title
            font-size: 6vw
            line-height: 6.2vw

        &__text
            font-size: 3.4vw
            line-height: 4.6vw

        &__button
            font-size: 3.4vw
            line-height: 4.6vw
            width: 39.4vw
            height: 10.3vw

</style>