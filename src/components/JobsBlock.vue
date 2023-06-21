<template>
    <section class="jobs" id="jobs">
        <div class="jobs__content">
            <div class="job job_1"></div>
            <div class="job job_2"></div>
        </div>
    </section>
</template>

<script>
export default {
    name: 'JobsBlock',
    props: {

    }    
}
</script>

<style lang="sass">
.jobs
    background: $white-bg
    width: 100%
    padding-top: 72px
    padding-bottom: 100px

    display: flex
    align-items: center
    justify-content: center

    &__content
        width: 70%
        display: flex
        flex-direction: row
        align-items: center
        justify-content: center

        gap: 30px

.job
    background: url(@/assets/job.png)
    background-repeat: no-repeat
    background-size: contain
    background-position: center
    width: 255px
    height: 120px

    &_1
        background: url(@/assets/rocketFirm-logo.png)
        background-repeat: no-repeat
        background-size: contain
        background-position: center

    
    &_2
        background: url(@/assets/arcana-logo.png)
        background-repeat: no-repeat
        background-size: contain
        background-position: center


@media screen and (max-width: 1200px)
    .jobs
        &__content
            width: 80%
            justify-content: space-between
            gap: 0
    .job
        width: 15vw
        height: 7vw

@media screen and (max-width: 600px)
    .jobs
        padding-top: 36px
        padding-bottom: 50px
        &__content
            width: 80%
            flex-direction: column
            align-items: center
            gap: 15px

    .job
        width: 30vw
        height: 14vw
</style>