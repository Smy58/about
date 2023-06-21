<template>
  <HeaderPage :scrolled="scrolled"/>
  <MainBlock v-on:setScroll="setScroll"/>
  <AboutBlock v-on:setScroll="setScroll"/>
  <NumbersBlock />
  <SkillBlock />
  <VideoBlock v-on:setScroll="setScroll" />
  <ProjectsBlock v-on:setScroll="setScroll" />
  <JobsBlock />
  <FormBlock v-on:setScroll="setScroll" />
  <FooterPage />
</template>

<script>
import HeaderPage from './components/HeaderPage.vue';
import MainBlock from './components/MainBlock.vue';
import AboutBlock from './components/AboutBlock.vue';
import NumbersBlock from './components/NumbersBlock.vue';
import SkillBlock from './components/SkillBlock.vue';
import VideoBlock from './components/VideoBlock.vue';
import ProjectsBlock from './components/ProjectsBlock.vue';
import JobsBlock from './components/JobsBlock.vue';
import FormBlock from './components/FormBlock.vue';
import FooterPage from './components/FooterPage.vue';

export default {
  name: 'App',
  components: {
    HeaderPage,
    MainBlock,
    AboutBlock,
    NumbersBlock,
    SkillBlock,
    VideoBlock,
    ProjectsBlock,
    JobsBlock,
    FormBlock,
    FooterPage
  },
  data() {
    return {
      scrolled: 1  
    }
  },
  methods: {
    setScroll(newScroll) {
      if (newScroll != 0 ){
        this.scrolled = newScroll
      }
    }
  }
}
</script>

<style lang="sass">
#app
  display: flex
  flex-direction: column
  align-items: center
</style>
