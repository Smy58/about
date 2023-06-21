<template>
    <header class="header">
        <div class="header__content">
            <div class="header__logo"></div>
            <div class="header__nav">
                <a href="#main" :class="'header__link ' + (scrolled == 1 ? 'header__link_active' : '')" v-on:click="onLink">Главная</a>
                <a href="#about" :class="'header__link ' + (scrolled == 2 ? 'header__link_active' : '')" v-on:click="onLink">Об авторе</a>
                <a href="#vidblock" :class="'header__link ' + (scrolled == 4 ? 'header__link_active' : '')" v-on:click="onLink">Процесс</a>
                <a href="#projects" :class="'header__link ' + (scrolled == 3 ? 'header__link_active' : '')" v-on:click="onLink">Работы</a>
                <a href="#form-block" :class="'header__link ' + (scrolled == 5 ? 'header__link_active' : '')" v-on:click="onLink">Контакты</a>
            </div>
        </div>

        <div class="header__button" v-on:click="onMenu"></div>

        <div :class="isMenu ? 'header__mobile' : 'header__mobile header__mobile_hidden'">
            <div class="header__nav header__nav_mobile">
                <div class="header__close" v-on:click="onMenu"></div>
                <a href="#main" :class="'header__link ' + (scrolled == 1 ? 'header__link_active' : '')" v-on:click="onMobileLink">Главная</a>
                <a href="#about" :class="'header__link ' + (scrolled == 2 ? 'header__link_active' : '')" v-on:click="onMobileLink">Об авторе</a>
                <a href="#vidblock" :class="'header__link ' + (scrolled == 4 ? 'header__link_active' : '')" v-on:click="onMobileLink">Процесс</a>
                <a href="#projects" :class="'header__link ' + (scrolled == 3 ? 'header__link_active' : '')" v-on:click="onMobileLink">Работы</a>
                <a href="#form-block" :class="'header__link ' + (scrolled == 5 ? 'header__link_active' : '')" v-on:click="onMobileLink">Контакты</a>
            </div>
        </div>
        
    </header>
</template>

<script>
    export default {
        name: 'HeaderPage',
        data() {
            return {
                isMenu: false,
                
            }
        },
        props: {
            scrolled: Number
        },
        methods: {
            onMenu() {
                this.isMenu = !this.isMenu
            },
            onLink(ev) {
                ev.preventDefault();
                const blockID = ev.target.getAttribute('href');
                document.querySelector('' + blockID).scrollIntoView({
                    behavior: 'smooth',
                    block: "start"
                })
                console.log('link');
                window.dispatchEvent( new CustomEvent('scroll', {}));
            },
            onMobileLink() {
                this.onMenu();
                this.onLink();
            }

        }
    }
</script>


<style lang="sass">

.header 
    width: 100%
    height: 120px
    position: fixed
    top: 0
    left: 0
    display: flex
    overflow-x: hidden
    background: $main-bg
    z-index: 10000
    flex:
        direction: column
    align:
        items: center

    &__mobile
        display: none
    
    &__button
        display: none

    &__content
        width: 1200px
        height: 100%
        display: flex
        flex:
            direction: row
        align-items: center
        justify-content: space-between
    
    &__logo
        width: 96px
        height: 60px
        background: url(@/assets/logo.png)
        background:
            repeat: no-repeat
            size: contain
        
    &__link
        font-family: 'Roboto'
        font:
            style: normal
            weight: $nav-fw
            size: $nav-fz
        line-height: $nav-lh
        letter-spacing: 0.1em
        text:
            decoration: none
            transform: uppercase
        margin-right: 42px
        color: $black

        transition: color 0.4s ease, font-size 0.4s ease

        &_active 
            font-weight: $nav-fw-active
            color: $dark-blue
            font-size: $nav-fz-active

        
        &:last-child
            margin: 0

@media screen and (max-width: 1250px)
    .header
        &__content
            width: 85%
        
        &__link 
            margin-right: 28px
        &__logo
            width: 73px
            height: 41px

       

@media screen and (max-width: 830px)
    .header
        
        &__mobile
            display: flex
            position: fixed
            top: 0
            left: 0
            width: 100%
            transform: translateX(0)
            z-index: 100000

            transition: transform 0.5s ease

            &_hidden
                transform: translateX(100%)

            
        &__nav
            display: none
            &_mobile
                width: 100%
                display: flex
                flex-direction: column
                align-items: center
                background: $white-bg
                padding-top: 50px
                padding-bottom: 50px

                gap: 20px
    
        &__link
            margin: 0

        &__button
            display: block
            position: absolute
            top: 40px
            right: 40px

            width: 35px
            height: 35px

            background: url(@/assets/menu.png)
            background-repeat: no-repeat
            background-size: contain

        &__close
            display: block
            position: absolute
            top: 25px
            right: 30px

            width: 20px
            height: 20px

            background: url(@/assets/close.png)
            background-repeat: no-repeat
            background-size: contain

</style>