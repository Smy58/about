<template>
    <section class="form-block" id="form-block">
        <form action="" class="form">
            <h2 class="form__title">Хотите веб-сайт⁇</h2>
            <p class="form__text">Lorem Ipsum - это текст-"рыба", часто используемый в печати и вэб-дизайне. Lorem Ipsum является стандартной "рыбой" для текстов на латинице с начала XVI века.</p>
            <div class="form__inputs">
                <input type="text" name="name" id="name" class="form__input" placeholder="Ваше имя">
                <input type="email" name="email" id="email" class="form__input" placeholder="Ваше email">
            </div>
            <textarea name="" id="" cols="30" rows="10" class="form__area" placeholder="Сообщение"></textarea>
            <input type="submit" class="form__submit">
        </form>
    </section>
</template>

<script>
export default {
    name: 'FormBlock',
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
            let obj = document.querySelector('#form-block');
            let {top} = obj.getBoundingClientRect();
            let height = document.documentElement.clientHeight;
            this.$emit('setScroll', (top < (height * 0.55) && top >= 0 ) ? 5 : 0 );
        }
    } 
}
</script>

<style lang="sass">
.form-block
    margin-top: 100px
    margin-bottom: 100px

    width: 100%
    display: flex
    flex-direction: column
    align-items: center

.form
    width: 540px
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
        font-weight: 400
        font-size: 16px
        line-height: 26px
        text-align: center

        color: $grey
        margin-bottom: 65px

    &__inputs
        display: flex
        flex-direction: row
        align-items: center
        gap: 30px

        margin-bottom: 20px

    &__input
        width: 255px
        height: 50px
        border: none
        background: #fff

        font-weight: 400
        font-size: 14px
        line-height: 23px
        color: $input-color
        padding-left: 20px

    &__area
        width: 540px
        height: 175px
        background: #fff
        border: none

        padding-left: 20px
        padding-top: 17px

        font-family: 'Roboto'
        font-style: normal
        font-weight: 400
        font-size: 14px
        line-height: 23px
        color: $input-color

        margin-bottom: 50px

    &__submit
        width: 190px
        height: 55px
        background: $blue-button

        font-weight: 400
        font-size: 14px
        line-height: 23px
        text-align: center
        text-transform: uppercase
        letter-spacing: 0.15em
        color: $button-text

        border: none

@media screen and (max-width: 600px)
    .form-block
        margin-top: 50px
        margin-bottom: 50px
        
    .form
        
        width: 90%
        
        &__inputs
            flex-direction: column
            gap: 0

            width: 100%
        
        &__input
            width: 100%

            margin-bottom: 20px
            
        &__area
            width: 100%
</style>