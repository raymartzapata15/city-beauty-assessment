<template>
    <div class="cb-quiz-6">
        <h2>How much time do you spend on body care daily:</h2>
    <input type="radio" v-model="selectedValue" :value="1" style="display: none;">
        <div 
            class="cb-card" 
            @click="setChecked(1)" :class="{ 'selected': selectedValue === 1 }"
        >
            <label class="cb-radio">10 Minutes
                <input 
                    type="radio"
                    checked="checked" 
                    :value="1"
                    @click="setChecked(1)" :class="{ 'selected': selectedValue === 1 }"
                    v-model="selectedValue"
                >
                <span class="cb-radio-checkmark"></span>
            </label>
        </div>
        <div 
            class="cb-card"
            @click="setChecked(2)" :class="{ 'selected': selectedValue === 2 }"
        >
            <label class="cb-radio">30 Minutes
                <input 
                    type="radio" 
                    @click="setChecked(2)" :class="{ 'selected': selectedValue === 2 }"
                    :value="2"
                    v-model="selectedValue"
                >
                <span class="cb-radio-checkmark"></span>
            </label>
        </div>
        <div 
            class="cb-card"
            @click="setChecked(3)" :class="{ 'selected': selectedValue === 3 }"
        >
            <label class="cb-radio">1 Hour
                <input 
                    type="radio" 
                    @click="setChecked(3)" :class="{ 'selected': selectedValue === 3 }"
                    :value="3"
                    v-model="selectedValue"
                >
                <span class="cb-radio-checkmark"></span>
            </label>
        </div>
        <div 
            class="cb-card"
            @click="setChecked(4)" :class="{ 'selected': selectedValue === 4 }"
        >
            <label class="cb-radio">5 Minutes
                <input 
                    type="radio" 
                    @click="setChecked(4)" :class="{ 'selected': selectedValue === 4 }"
                    :value="4"
                    v-model="selectedValue"
                >
                <span class="cb-radio-checkmark"></span>
            </label>
        </div>
        <div class="cb-button-container">
            <button :disabled="!buttonActivated" @click="$emit('next')" class="cb-button-continue">
                <p>Continue</p>
                <img src="../assets/images/arrow.png" alt="Arrow Right">
            </button>
            <a class="cb-button-skip">
                <p>Skip</p>
            </a>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Question6',
    data() {
        return {
            selectedValue: null,
            buttonActivated: false
        };
    },
    methods: {
        setChecked(value) {
            if (this.selectedValue === value) {
                this.selectedValue = null;
            } else {
                this.selectedValue = value;
            }
            this.buttonActivated = true;
        }
    }
}
</script>

<style scoped>
.cb-quiz-6 {
    display: flex;
    justify-content: center;
    flex-direction: column;
    margin: 32px auto 0;
    width: 517px;
}

.cb-quiz-6 h2 {
    margin-bottom: 32px;
}

.cb-card {
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    padding-right: 48px;
    height: 81px;
}

.cb-card p {
    padding-left: 50px;
    margin-top: 10px;
}

.cb-card-unsure {
    justify-content: start;
    flex-direction: row;
    align-items: center;
}

.cb-card-unsure h3 {
    padding-left: 25px;
}

.cb-card-unsure img {
    height: 24px;
}

.cb-border {
    margin: 15px 0 30px;
}

@media only screen and (max-width: 1024px) {
    .cb-quiz-6 {
        align-items: center;
        padding: 0 20px;
        width: auto;
    }

    .cb-card {
        padding: 24px 14px 16px 24px;
    }

    .label-1,
    .label-2 {
        width: 43%;
    }

    .label-3 {
        width: 100%;
    }

    .label-4 {
        width: 30%;
    }
}
</style>