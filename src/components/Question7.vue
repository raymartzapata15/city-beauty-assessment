<template>
    <div class="cb-quiz-2">
        <h2>What hydrating ingredients are you interested in?</h2>
        <div 
            class="cb-card" 
            :class="{ 'selected': isChecked[1] }"
            @click="toggleCheckbox(1)"
        >
            <label class="cb-checkbox">Overwhelmed, too many products to keep track of 
                <input 
                    type="checkbox" 
                    v-model="isChecked[1]" 
                    @click="toggleCheckbox(1)"
                >
                <span class="cb-checkmark"></span>
            </label>
        </div>
        <div 
            class="cb-card"
            :class="{ 'selected': isChecked[2] }"
            @click="toggleCheckbox(2)"
        >
            <label class="cb-checkbox">Overcomplicated, hard to understand ingredients 
                <input 
                    type="checkbox" 
                    v-model="isChecked[2]" 
                    @click="toggleCheckbox(2)"
                >
                <span class="cb-checkmark"></span>
            </label>
        </div>
        <div 
            class="cb-card"
            :class="{ 'selected': isChecked[3] }"
            @click="toggleCheckbox(3)"
        >
            <label class="cb-checkbox">Hopelessness
                <input 
                    type="checkbox" 
                    v-model="isChecked[3]"
                    @click="toggleCheckbox(3)"
                >
                <span class="cb-checkmark"></span>
            </label>
        </div>
        <div 
            class="cb-card"
            :class="{ 'selected': isChecked[4] }"
            @click="toggleCheckbox(4)"
        >
            <label class="cb-checkbox">No Results
                <input 
                    type="checkbox" 
                    v-model="isChecked[4]"
                    @click="toggleCheckbox(4)"
                >
                <span class="cb-checkmark"></span>
            </label>
        </div>
        <div 
            class="cb-card"
            :class="{ 'selected': isChecked[5] }"
            @click="toggleCheckbox(5)"
        >
            <label class="cb-checkbox">Anxiety
                <input 
                    type="checkbox" 
                    v-model="isChecked[5]"
                    @click="toggleCheckbox(5)"
                >
                <span class="cb-checkmark"></span>
            </label>
        </div>
        <hr class="cb-border">
        <div 
            class="cb-card cb-card-unsure"
            :class="{ 'selected': isChecked[6] }"
            @click="toggleCheckbox(6)"
        >
            <img src="../assets/images/close.png" alt="Unsure what my skin needs">
            <h3>None of the Above</h3>
        </div>
        <div class="cb-button-container">
            <button :disabled="!buttonActivated" @click="showThanksCard" class="cb-button-continue">
                <p>Continue</p>
                <img src="../assets/images/arrow.png" alt="Arrow Right">
            </button>
            <a @click="showThanksCard" class="cb-button-skip">
                <p>Skip</p>
            </a>
        </div>
        <div v-if="isThanksCardShow" class="cb-thanks-card">
            <h3>Thanks for sharing!</h3>
            <p>
                We've discovered that a lot of people have faced the same setbacks. City Beauty has 
                a clear one-step treatment that is easy to follow with long-term results. 
                In less than two minutes, you will feel better than ever. 
            </p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Question7',
    data() {
        return {
            isChecked: { 1: false, 2: false, 3: false, 4: false, 5: false, 6: false },
            isThanksCardShow: false,
            buttonActivated: false
        };
    },
    computed: {
        isButtonEnabled() {
            return Object.values(this.isChecked).some(value => value);
        }
    },
    methods: {
        toggleCheckbox(checkboxNumber) {
            this.isChecked[checkboxNumber] = !this.isChecked[checkboxNumber];
            this.buttonActivated = this.isButtonEnabled;
        },
        showThanksCard() {
            this.isThanksCardShow = true;
        }
    }
}
</script>

<style scoped>
.cb-quiz-2 {
    display: flex;
    justify-content: center;
    flex-direction: column;
    margin: 32px auto 0;
    width: 517px;
}

.cb-quiz-2 h2 {
    margin-bottom: 32px;
}

.cb-card {
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    padding-right: 48px;
    height: 92px;
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

.cb-thanks-card {
    border: 2px solid rgba(255,255,255,0.3);
    background-color: transparent;
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 42px 52px 42px 33px;
    margin-top: 48px;
}

.cb-thanks-card h3 {
    margin-bottom: 10px;
}

.cb-thanks-card p {
    line-height: 21px;
}

@media only screen and (max-width: 1024px) {
    .cb-quiz-2 {
        align-items: center;
        padding: 0 20px;
        width: auto;
    }

    .cb-card {
        height: 97px;
        padding: 24px 0 16px 18px;
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