<template>
    <div class="cb-quiz-1">
        <h2>Select problem areas</h2>
        <div 
            class="cb-card"
            :class="{ 'selected': isChecked[1] }"
            @click="toggleCheckbox(1)"
        >
            <label class="cb-checkbox label-1">Loose skin on thighs and legs
                <input 
                    type="checkbox"
                    v-model="isChecked[1]" 
                    @click="toggleCheckbox(1)"
                >
                <span class="cb-checkmark"></span>
            </label>
            <img 
                class="cb-card-display-image" 
                src="../assets/images/page-1/pg-1-thighs.png" 
                alt="Loose skin on thighs and legs"
            >
        </div>
        <div 
            class="cb-card"
            :class="{ 'selected': isChecked[2] }"
            @click="toggleCheckbox(2)"
        >
            <label class="cb-checkbox label-2">Thinning skin on arms
                <input 
                    type="checkbox" 
                    v-model="isChecked[2]" 
                    @click="toggleCheckbox(2)"
                >
                <span class="cb-checkmark"></span>
            </label>
            <img 
                class="cb-card-display-image" 
                src="../assets/images/page-1/pg-1-thin-arms.png" 
                alt="Thinning skin on arms"
            >
        </div>
        <div 
            class="cb-card"
            :class="{ 'selected': isChecked[3] }"
            @click="toggleCheckbox(3)"
        >
            <label class="cb-checkbox label-3">Loose neck/jaw
                <input 
                    type="checkbox" 
                    v-model="isChecked[3]" 
                    @click="toggleCheckbox(3)"
                >
                <span class="cb-checkmark"></span>
            </label>
            <img 
                class="cb-card-display-image"
                src="../assets/images/page-1/pg-1-loose-neck.png" 
                alt="Loose neck/jaw"
            >
        </div>
        <div 
            class="cb-card"
            :class="{ 'selected': isChecked[4] }"
            @click="toggleCheckbox(4)"
        >
            <label class="cb-checkbox label-4">Saggy belly
                <input 
                    type="checkbox"
                    v-model="isChecked[4]" 
                    @click="toggleCheckbox(4)"
                >
                <span class="cb-checkmark"></span>
            </label>
            <img 
                class="cb-card-display-image" 
                src="../assets/images/page-1/pg-1-saggy-belly.png" 
                alt="Saggy belly"
            >
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
    name: 'Question1',
    data() {
        return {
            isChecked: { 1: false, 2: false, 3: false, 4: false },
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
    }
}
</script>

<style scoped>
.cb-quiz-1 {
    display: flex;
    justify-content: center;
    flex-direction: column;
    margin: 32px auto 0;
    width: 517px;
}

.cb-quiz-1 h2 {
    margin-bottom: 32px;
}

@media only screen and (max-width: 1024px) {
    .cb-quiz-1 {
        align-items: center;
        padding: 0 20px;
        width: auto;
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