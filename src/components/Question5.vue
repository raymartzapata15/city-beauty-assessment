<template>
    <div class="cb-quiz-5">
        <h2>How often do you moisturize your skin?</h2>
        <p class="cb-slider-label">Choose your current level to align with your routine:</p>

        <div class="cb-tooltip-container">
            <div class="cb-tooltip-label-top">
                <p>1</p>
                <p>10</p>
            </div>
            <div class="cb-tooltip" :style="{ left: `${(sliderValue - 1) * 11}%` }">{{ getTooltipName(sliderValue) }}</div>
            <div class="cb-range">
                <input 
                    type="range" 
                    v-model="sliderValue" 
                    min="1" 
                    max="10" 
                    @input="updateChoice" 
                    class="cb-range-slider"
                />
            </div>
            <div class="cb-range-labels">
                <div class="cb-newcomer-1"></div>
                <div class="cb-newcomer-2"></div>
                <div class="cb-newcomer-3"></div>
                <div class="cb-newcomer-4"></div>
                <div class="cb-amateur-5"></div>
                <div class="cb-amateur-6"></div>
                <div class="cb-amateur-7"></div>
                <div class="cb-pro-8"></div>
                <div class="cb-pro-9"></div>
                <div class="cb-pro-10"></div>
            </div>
            <div class="cb-tooltip-label">
                <p>Newcomer</p>
                <p>Pro</p>
            </div>
        </div>

        <div v-if="sliderValue === 1" class="cb-card-result">
            <h3>Newcomer</h3>
            <p>Whenever I touch my skin it feels flaky, but I leave it alone</p>
        </div>
        <div v-if="sliderValue === 2" class="cb-card-result">
            <h3>Newcomer</h3>
            <p>I have applied lotion before to my dry, crepey skin (Rarely)</p>
        </div>
        <div v-if="sliderValue === 3" class="cb-card-result">
            <h3>Newcomer</h3>
            <p>I do apply lotion/cream sometimes on dry skin</p>
        </div>
        <div v-if="sliderValue === 4" class="cb-card-result">
            <h3>Newcomer</h3>
            <p>I do apply lotion/cream to my skin to feel moisturized</p>
        </div>
        <div v-if="sliderValue === 5" class="cb-card-result">
            <h3>Amateur</h3>
            <p>I try to apply lotion/cream, but still not regularly </p>
        </div>
        <div v-if="sliderValue === 6" class="cb-card-result">
            <h3>Amateur</h3>
            <p>I apply lotion/cream fairly regularly, at least once a week</p>
        </div>
        <div v-if="sliderValue === 7" class="cb-card-result">
            <h3>Amateur</h3>
            <p>I apply lotion/cream after every shower consistently for the last 1-3 months</p>
        </div>
        <div v-if="sliderValue === 8" class="cb-card-result">
            <h3>Pro</h3>
            <p>I'm committed to moisturize my skin whenever I can</p>
        </div>
        <div v-if="sliderValue === 9" class="cb-card-result">
            <h3>Pro</h3>
            <p>Oh, trust me. I deeply hydrate my skin, but I want to take it to the next level</p>
        </div>
        <div v-if="sliderValue === 10" class="cb-card-result">
            <h3>Pro</h3>
            <p>I'm on fire. Deeply hydrating my skin every day is a must to stimulate collagen/elastin </p>
        </div>

        <div class="cb-button-container">
            <button @click="$emit('next')" class="cb-button-continue">
                <p>Continue</p>
                <img src="../assets/images/arrow.png" alt="Arrow Right">
            </button>
            <a @click="$emit('next')" class="cb-button-skip">
                <p>Skip</p>
            </a>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            sliderValue: 1,
        }
    },
    methods: {
        updateChoice() {
            this.sliderValue = Math.round(this.sliderValue);
        },
        getTooltipName(value) {
            switch (value) {
                case 1:
                    return '1';
                case 2:
                    return '2';
                case 3:
                    return '3';
                case 4:
                    return '4';
                case 5:
                    return '5';
                case 6:
                    return '6';
                case 7:
                    return '7';
                case 8:
                    return '8';
                case 9:
                    return '9';
                case 10:
                    return '10';
                default:
                return '';
            }
        },
    }
}
</script>

<style scoped>
.cb-quiz-5 {
    display: flex;
    justify-content: center;
    flex-direction: column;
    margin: 90px auto 0;
    width: 519px;
}

.cb-quiz-5 h2 {
    margin-bottom: 39px;
}

.cb-card-result {
    height: 135px;
    background-color: #556579;
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding-left: 33px;
    margin-bottom: 17px;
}

.cb-card-result h3 {
    margin-bottom: 10px;
}

.cb-image {
    width: auto;
    height: 496px;
}

.cb-range {
    position: relative;
    width: 519px;
    height: 7px;
}

.cb-range-slider {
    -webkit-appearance: none;
    width: 100%;
    height: 7px;
    background: transparent;
    position: absolute;
    top: 0;
    margin: 0;
    z-index: 99;
}

.cb-range-slider::-webkit-slider-thumb {
    -webkit-appearance: none;
    appearance: none;
    width: 25px;
    height: 25px;
    border-radius: 50px;
    background: #86919F;
    cursor: pointer;
    z-index: 99;
    position: relative;
}

.cb-range-slider::-moz-range-thumb {
    width: 25px;
    height: 25px;
    border-radius: 50px;
    background: #86919F;
    cursor: pointer;
}

.cb-range-labels {
    margin: 0;
    padding: 0;
    display: flex;
    justify-content: space-between;
    gap: 2px;
    overflow-x: clip;
    width: 517px;
}

.cb-range-labels div {
    position: relative;
    width: 100%;
}

.cb-range-labels div::before {
    content: "";
    position: absolute;
    top: -7px;
    margin: 0;
    height: 7px;
    width: 100%;
}

.cb-range-labels .cb-newcomer-1::before {
    background-color: rgba(255,255,255,0.1);
}
.cb-range-labels .cb-newcomer-2::before {
    background-color: rgba(255,255,255,0.2);
}
.cb-range-labels .cb-newcomer-3::before {
    background-color: rgba(255,255,255,0.3);
}
.cb-range-labels .cb-newcomer-4::before {
    background-color: rgba(255,255,255,0.4);
}
.cb-range-labels .cb-amateur-5::before {
    background-color: rgba(255,255,255,0.5);
}
.cb-range-labels .cb-amateur-6::before {
    background-color: rgba(255,255,255,0.6);
}
.cb-range-labels .cb-amateur-7::before {
    background-color: rgba(255,255,255,0.7);
}
.cb-range-labels .cb-pro-8::before {
    background-color: rgba(255,255,255,0.8);
}
.cb-range-labels .cb-pro-9::before {
    background-color: rgba(255,255,255,0.9);
}
.cb-range-labels .cb-pro-10::before {
    background-color: rgba(255,255,255,1);
}

.cb-range-labels .cb-pro-10 {
    width: 0;
}

.cb-tooltip-container {
    position: relative;
    width: 100%;
    margin: 54px 0 32px;
    width: 519px;
}

.cb-tooltip {
    background-color: #546578;
    color: #fff;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 16px;
    letter-spacing: 0;
    line-height: 17px;
    position: absolute;
    bottom: 85%;
    left: 0%;
    transform: translateX(-50%);
    padding: 0 6px;
    height: 29px;
    width: 25px;
}

.cb-tooltip::before {
    content: "";
    position: absolute;
    bottom: -8px;
    left: 50%;
    border: 10px solid #546578;
    border-bottom: none;
    border-left-color: transparent;
    border-right-color: transparent;
    transform: translateX(-50%);
}

.cb-tooltip-label,
.cb-tooltip-label-top {
    display: flex;
    justify-content: space-between;
    font-size: 16px;
    
}

.cb-tooltip-label {
    margin-top: 15px;
}

.cb-tooltip-label-top {
    margin-bottom: 15px;
}

.cb-tooltip-label p,
.cb-tooltip-label-top p {
    line-height: 1.2;
}

.cb-tooltip-label-right {
    text-align: right;
}

@media only screen and (max-width: 1024px) {
    .cb-quiz-5 {
        flex-direction: column;
        margin: 28px auto 0;
        padding: 0 20px;
        width: auto;
    }

    .cb-tooltip-container {
        width: 100%;
    }

    .cb-range {
        width: 100%;
    }
}
</style>