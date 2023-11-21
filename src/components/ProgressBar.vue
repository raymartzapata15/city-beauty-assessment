<template>
    <div v-if="showProgressBar" class="progress-bar-container">
        <div class="progress-bar">
            <button @click="goBack"><img src="../assets/images/back-arrow.png" alt="Arrow Back"></button>
            <div class="progress">
                <div class="progress-inner" :style="{ width: progressWidth }"></div>
            </div>
            <div class="progress-label">{{ currentStep }}/{{ totalSteps }}</div>
        </div>
    </div>
</template>
  
<script>
export default {
    props: {
        showProgressBar: {
            type: Boolean,
            default: true,
        },
        currentStep: {
            type: Number,
            required: true,
        },
        totalSteps: {
            type: Number,
            required: true,
        },
    },
    computed: {
        progressWidth() {
            return `${(this.currentStep / this.totalSteps) * 100}%`;
        },
    },
    methods: {
        goBack() {
            this.$emit('back');
        }
    }
};
</script>
  
<style>
.progress-bar-container {
    width: 507px;
    margin: 0 auto;
}

.progress-bar {
    display: flex;
    align-items: center;
    gap: 16px;
    margin-top: 39px;
    margin-bottom: 20px;
}

button {
    background-color: #556579;
    border: none;
    width: 26px;
}

.progress-bar button img {
    height: 21px;
    width: 11.5px;
}

.progress-label {
    color: #FFFFFF;
    font-family: "Work Sans";
    font-size: 16px;
    letter-spacing: 0;
    line-height: 17px;
}

.progress {
    height: 12px;
    background-color: #556579;
    border-radius: 0;
    overflow: hidden;
    width: 426px;
}

.progress-inner {
    height: 100%;
    background-color: #E2C47C; 
    transition: width 0.5s;
}

@media only screen and (max-width: 1024px) {
    .progress-bar-container {
        width: 329px;
        padding: 0 20px;
    }
}
</style>