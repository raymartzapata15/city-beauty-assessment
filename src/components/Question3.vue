<template>
    <div class="cb-quiz-3">
        <div class="cb-col-1 desk">
            <img v-if="sliderValue === 1" src="../assets/images/pg-3-normal-d.png" alt="Image 1" class="cb-image">
            <img v-if="sliderValue === 2" src="../assets/images/pg-3-dry-d.png" alt="Image 2" class="cb-image">
            <img v-if="sliderValue === 3" src="../assets/images/pg-3-microwrinkles-d.png" alt="Image 3" class="cb-image">
            <img v-if="sliderValue === 4" src="../assets/images/pg-3-scaly-d.png" alt="Image 4" class="cb-image">
            <img v-if="sliderValue === 5" src="../assets/images/pg-3-itchy-d.png" alt="Image 5" class="cb-image">
            <img v-if="sliderValue === 6" src="../assets/images/pg-3-crepey-d.png" alt="Image 5" class="cb-image">
        </div>
        <div class="cb-col-1 mobile">
            <h2>How would you describe your skin?</h2>
            <img v-if="sliderValue === 1" src="../assets/images/pg-3-normal-m.jpg" alt="Image 1" class="cb-image">
            <img v-if="sliderValue === 2" src="../assets/images/pg-3-dry-m.jpg" alt="Image 2" class="cb-image">
            <img v-if="sliderValue === 3" src="../assets/images/pg-3-microwrinkles-m.jpg" alt="Image 3" class="cb-image">
            <img v-if="sliderValue === 4" src="../assets/images/pg-3-scaly-m.jpg" alt="Image 4" class="cb-image">
            <img v-if="sliderValue === 5" src="../assets/images/pg-3-itchy-m.jpg" alt="Image 5" class="cb-image">
            <img v-if="sliderValue === 6" src="../assets/images/pg-3-crepey-m.jpg" alt="Image 5" class="cb-image">
        </div>
        <div class="cb-col-2">
            <h2>How would you describe your skin?</h2>
            <div class="cb-tooltip-container">
                <div class="cb-tooltip" :style="{ left: `${(sliderValue - 1) * 20}%` }">{{ getTooltipName(sliderValue) }}</div>
                <div class="cb-range">
                    <input 
                        type="range" 
                        v-model="sliderValue" 
                        min="1" 
                        max="6" 
                        @input="updateImage" 
                        class="cb-range-slider"
                    />
                </div>
                <div class="cb-range-labels">
                    <div></div>
                    <div></div>
                    <div></div>
                    <div></div>
                    <div></div>
                    <div></div>
                </div>
                <div class="cb-tooltip-label">
                    <p>Normal <br> Skin</p>
                    <p class="cb-tooltip-label-right">Crepey <br> Skin</p>
                </div>
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
    </div>
</template>

<script>
export default {
    name: 'Question3',
    data() {
        return {
            sliderValue: 1,
        };
    },
    methods: {
        updateImage() {
            this.sliderValue = Math.round(this.sliderValue);
        },
        getTooltipName(value) {
            switch (value) {
                case 1:
                    return 'Normal Skin';
                case 2:
                    return 'Dry Skin';
                case 3:
                    return 'Microwrinkles';
                case 4:
                    return 'Scaly, Rough Skin';
                case 5:
                    return 'Itchy, Irritated Skin';
                case 6:
                    return 'Crepey Skin';
                default:
                return '';
            }
        },
    }
}
</script>

<style scoped>
.cb-quiz-3 {
    display: flex;
    justify-content: center;
    flex-direction: row;
    gap: 80px;
    margin: 32px auto 0;
}

.cb-col-2 {
    display: flex;
    flex-direction: column;
    justify-content: center;
    width: 517px;
}

.cb-quiz-3 h2 {
    margin-bottom: 32px;
}

.cb-range-slider {
  width: 100%;
}

.cb-image {
    width: auto;
    height: 496px;
}

.cb-range {
    position: relative;
    width: 413px;
    height: 7px;
}

.cb-range-labels {
    margin: 0;
    padding: 0;
    list-style: none;
    display: flex;
    justify-content: space-between;
}

.cb-range-labels div {
    position: relative;
    float: left;
    width: auto;
    text-align: center;
    color: transparent;
    font-size: 14px;
    cursor: pointer;
}

.cb-range-labels div::before {
    content: "";
    position: absolute;
    top: -7px;
    margin: 0;
    width: 2px;
    height: 7px;
    background: #0C233F;
}

.cb-range-slider {
    -webkit-appearance: none;
    width: 100%;
    height: 7px;
    background: #546578;
    position: absolute;
    top: 0;
    margin: 0;
}

.cb-range-slider::-webkit-slider-thumb {
    -webkit-appearance: none;
    appearance: none;
    width: 25px;
    height: 25px;
    border-radius: 50px;
    background: #E2C47C;
    cursor: pointer;
    z-index: 99;
    position: relative;
}

.cb-range-slider::-moz-range-thumb {
    width: 25px;
    height: 25px;
    border-radius: 50px;
    background: #E2C47C;
    cursor: pointer;
}

.cb-tooltip-container {
    position: relative;
    width: 100%;
    margin: 48px 0 32px;
    width: 413px;
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
    bottom: 140%;
    left: 0%;
    transform: translateX(-50%);
    padding: 0 6px;
    height: 29px;
    width: max-content;
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

.cb-tooltip-label {
    display: flex;
    justify-content: space-between;
    font-size: 16px;
    margin-top: 15px;
}

.cb-tooltip-label p {
    line-height: 1.2;
}

.cb-tooltip-label-right {
    text-align: right;
}

.mobile {
    display: none;
}

.cb-col-1.desk {
    width: 141px;
    height: 496px;
}

@media only screen and (max-width: 1024px) {
    .cb-quiz-3 {
        align-items: center;
        flex-direction: column;
        gap: 32px;
        padding: 0 20px;
        width: auto;
    }

    .cb-col-2 {
        width: auto;
    }

    .cb-col-2 h2 {
        display: none;
    }

    .cb-tooltip-container {
        width: 238px;
        margin: 48px auto 32px;
    }

    .cb-range {
        width: 238px;
    }

    .desk {
        display: none;
    }

    .mobile {
        display: block;
    }

    .mobile .cb-image {
        height: 278px;
        width: 335px;
    }
    
}
</style>