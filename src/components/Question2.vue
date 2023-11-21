<template>
    <div class="cb-quiz-2">
        <h2>What hydrating ingredients are you interested in?</h2>
        <div 
            class="cb-card" 
            :class="{ 'selected': isChecked[1] }"
            @click="toggleCheckbox(1)"
        >
            <label class="cb-checkbox">Niacinamide
                <input 
                    type="checkbox" 
                    v-model="isChecked[1]" 
                    @click="toggleCheckbox(1)"
                >
                <span class="cb-checkmark"></span>
            </label>
            <p>This is a form of vitamin B that supports protein and collagen to promote optimal skin health</p>
        </div>
        <div 
            class="cb-card"
            :class="{ 'selected': isChecked[2] }"
            @click="toggleCheckbox(2)"
        >
            <label class="cb-checkbox">Lipid Compound
                <input 
                    type="checkbox" 
                    v-model="isChecked[2]" 
                    @click="toggleCheckbox(2)"
                >
                <span class="cb-checkmark"></span>
            </label>
            <p>This improves moisture retention in the skin’s barrier for long-lasting hydration</p>
        </div>
        <div 
            class="cb-card"
            :class="{ 'selected': isChecked[3] }"
            @click="toggleCheckbox(3)"
        >
            <label class="cb-checkbox">Ribose
                <input 
                    type="checkbox" 
                    v-model="isChecked[3]"
                    @click="toggleCheckbox(3)"
                >
                <span class="cb-checkmark"></span>
            </label>
            <p>This reduces the appearance of thinning, wrinkled skin</p>
        </div>
        <div 
            class="cb-card"
            :class="{ 'selected': isChecked[4] }"
            @click="toggleCheckbox(4)"
        >
            <label class="cb-checkbox">Jojoba Leaf Extract
                <input 
                    type="checkbox" 
                    v-model="isChecked[4]"
                    @click="toggleCheckbox(4)"
                >
                <span class="cb-checkmark"></span>
            </label>
            <p>This is rich in antioxidants and helps stimulate the production of collagen </p>
        </div>
        <div 
            class="cb-card"
            :class="{ 'selected': isChecked[5] }"
            @click="toggleCheckbox(5)"
        >
            <label class="cb-checkbox">Glycerin
                <input 
                    type="checkbox" 
                    v-model="isChecked[5]"
                    @click="toggleCheckbox(5)"
                >
                <span class="cb-checkmark"></span>
            </label>
            <p>This helps keep skin hydrated</p>
        </div>
        <hr class="cb-border">
        <div 
            class="cb-card cb-card-unsure"
            :class="{ 'selected': isChecked[6] }"
            @click="toggleCheckbox(6)"
        >
            <img src="../assets/images/close.png" alt="Unsure what my skin needs">
            <h3>Unsure what my skin needs</h3>
        </div>
        <div class="cb-button-container">
            <button :disabled="!buttonActivated" @click="$emit('next')" class="cb-button-continue">
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
    name: 'Question2',
    data() {
        return {
            isChecked: { 1: false, 2: false, 3: false, 4: false, 5: false, 6: false },
            isUnsure: false,
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
    height: 110px;
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

.cb-checkmark {
    top: 85%;
}

@media only screen and (max-width: 1024px) {
    .cb-quiz-2 {
        align-items: center;
        padding: 0 20px;
        width: auto;
    }

    .cb-card {
        height: 135px;
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