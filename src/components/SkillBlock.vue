<template>
    <section class="skill" id="skill">
        <div class="skill__content">
            <div class="skill__info">
                <h3 class="skill__title">Мои навыки</h3>
                <div class="skill__pos skill__pos_1">
                    <p class="skill__name">Adobe Photoshop</p>
                    <div class="skill__bar skill__bar_1">
                        <div :class="'skill__fill-bar ' + ( isLook ? 'skill__fill-bar_full' : '')"></div>
                    </div>
                </div>

                <div class="skill__pos skill__pos_2">
                    <p class="skill__name">Adobe Photoshop</p>
                    <div class="skill__bar skill__bar_2">
                        <div :class="'skill__fill-bar ' + ( isLook ? 'skill__fill-bar_full' : '')"></div>
                    </div>
                </div>

                <div class="skill__pos skill__pos_3">
                    <p class="skill__name">Adobe Photoshop</p>
                    <div class="skill__bar skill__bar_3">
                        <div :class="'skill__fill-bar ' + ( isLook ? 'skill__fill-bar_full' : '')"></div>
                    </div>
                </div>
            </div>
            <div class="skill__img"></div>
        </div>
    </section>
</template>

<script>
export default {
    name: 'SkillBlock',
    props: {
        
    },
    data() {
        return {
            isLook: false
        }
    },
    created() {
        window.addEventListener('scroll', this.handleScroll);
    },
    unmounted() {
        window.removeEventListener('scroll', this.handleScroll);
    },
    methods: {
        handleScroll() {
            let obj = document.querySelector('#skill');
            let {top} = obj.getBoundingClientRect();
            let height = document.documentElement.clientHeight;
            this.isLook = (top < (height * 0.45) && top >= 0 ) ? true : this.isLook ;
            console.log(this.isLook)

        }
    } 
}
</script>

<style lang="sass">
.skill
    background: $white-bg
    width: 100%
    display: flex
    flex-direction: column
    align-items: center
    justify-content: center
    padding-top: 101px
    padding-bottom: 101px

    &__content
        width: 1150px
        display: flex
        flex-direction: row
        align-items: center
        justify-content: space-between
    
    &__img
        background: url(@/assets/ava.png)
        background-repeat: no-repeat
        background-size: contain
        width: 555px
        height: 450px

    &__title
        font-weight: 500
        font-size: 32px
        line-height: 38px

        color: $black
        margin-bottom: 50px
    
    &__pos
        margin-bottom: 30px

    &__name
        font-weight: 400
        font-size: 16px
        line-height: 26px

        color: $grey
        margin-bottom: 20px

    &__bar
        width: 445px
        height: 4px

        background: $bar-color
        position: relative

    &__fill-bar
        position: absolute
        top: 0
        left: 0
        width: 0
        height: 4px

        background: $bar-color-fill
        transition: width 1s ease

        &_full
            width: 350px

@media screen and (max-width: 1200px)
    .skill
        &__content
            width: 90%
            flex-direction: column-reverse
        
        &__img
            margin-bottom: 40px

@media screen and (max-width: 600px)
    .skill
        padding-bottom: 50px
        padding-top: 50px
        &__img
            width: 90vw
            height: 73vw

        &__bar
            width: 80vw

        &__fill-bar
            width: 0

            &_full
                width: 50vw
        
</style>