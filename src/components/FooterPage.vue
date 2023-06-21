<template>
    <footer class="footer">
        <div class="footer__content">
            <div class="footer__info">
                <h3 class="footer__name">Ильшат Османов</h3>
                <p class="footer__copyright">(с) 2023. Все права защищены.</p>
            </div>
            <div class="footer__social">
                <a href="" class="footer__link footer__link_vk"></a>
                <a href="" class="footer__link footer__link_vk"></a>
                <a href="" class="footer__link footer__link_vk"></a>
            </div>
        </div>
    </footer>
</template>

<script>
export default {
    name: 'FooterPage',
    props: {

    }    
}
</script>

<style lang="sass">
.footer
    background: $blue-bg
    width: 100%
    padding-top: 50px
    padding-bottom: 50px

    display: flex
    align-items: center
    justify-content: center

    &__content
        width: 80%

        display: flex
        flex-direction: row
        justify-content: space-between
    
    &__name
        font-weight: 500
        font-size: 21px
        line-height: 25px
        color: #FFFFFF

        margin-bottom: 20px

    &__copyright
        font-weight: 400
        font-size: 13px
        line-height: 21px

        color: #FFFFFF

    &__social
        display: flex
        flex-direction: row
        align-items: center

        gap: 22px

    &__link 
        width: 43.75px
        height: 40px

        &_vk
            background: url(@/assets/vk.png)
            background-repeat: no-repeat
            background-size: contain


@media screen and (max-width: 600px)
    .footer
        &__social
            gap: 10px
            flex-wrap: wrap
        &__link
            width: 25px
            height: 25px
</style>