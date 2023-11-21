<template>
    <div class="cb-container">
        <div class="cb-header">
            <img src="./assets/images/city-beauty-logo.png" alt="City Beauty Logo">
        </div>

        <progress-bar 
            :showProgressBar="currentComponentIndex > skipCount"
            :currentStep="currentComponentIndex" 
            :totalSteps="components.length - 1"
            @back="goToPreviousComponent"
        />
        <div class="app" :class="{ 'fade': transitioning }">
            <component :is="currentComponent" @next="goToNextComponent" key="componentKey"></component>
        </div>
    </div>
</template>

<script>
import Intro from './components/Intro.vue'
import Question1 from './components/Question1.vue'
import Question2 from './components/Question2.vue'
import Question3 from './components/Question3.vue'
import Question4 from './components/Question4.vue'
import Question5 from './components/Question5.vue'
import Question6 from './components/Question6.vue'
import Question7 from './components/Question7.vue'
import ProgressBar from './components/ProgressBar.vue';

export default {
    name: 'App',
    components: {
        ProgressBar,
    },
    data() {
        return {
            components: [Intro, Question1, Question2, Question3, Question4, Question5, Question6, Question7],
            currentComponentIndex: 0,
            skipCount: 0,
            transitioning: false,
        };
    },
    computed: {
        currentComponent() {
            return this.components[this.currentComponentIndex];
        },
    },
    methods: {
        goToNextComponent() {
            this.transitioning = true;
            setTimeout(() => {
                if (this.currentComponentIndex < this.components.length - 1) {
                    this.currentComponentIndex++;
                } else {
                    console.warn('No more components');
                }
                this.transitioning = false;
            }, 500)
            
        },
        goToPreviousComponent() {
            if (this.currentComponentIndex > 0) {
                this.currentComponentIndex--;
            } else {
                console.log("No more previous components.");
            }
        },
    },
}
</script>

<style scoped>
.app {
  transition: opacity 0.5s;
}

.app.fade {
  opacity: 0.1;
}
</style>