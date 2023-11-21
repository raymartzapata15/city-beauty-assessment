<template>
    <div class="cb-quiz-4">
        <div class="cb-col-1">
            <img src="../assets/images/woman-crepe-halfway-there.gif" alt="Woman Crepey Skin" class="cb-image">
        </div>
        <div class="cb-col-2">
            <h3>Halfway there!</h3>
            <h2>Why do people give up protecting and hydrating their skin?</h2>
            <p class="cb-semi-bold">
                The No. 1 reason is using the wrong products that just aren't effective
            </p>
            <p>
                You'll achieve much more in just a few weeks of starting City Beauty's treatment.
            </p>
            <p>
                Our primary goal is to deliver deep, long-lasting hydration that will prevent harsh 
                aging and reduce the appearance of thinning, crepey skin. Visibly achieve healthy, 
                supple skin with us. 
            </p>
            <div class="cb-button-container">
                <button @click="$emit('next')" class="cb-button-continue">
                    <p>Got it</p>
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
    name: 'Question4',
}
</script>

<style scoped>
.cb-quiz-4 {
    display: flex;
    justify-content: center;
    flex-direction: row;
    gap: 43px;
    margin: 90px auto 0;
}

.cb-image {
    height: 367px;
    width: 408.62px;
}

.cb-col-2 {
    display: flex;
    flex-direction: column;
    justify-content: center;
    width: 442px;
}

.cb-quiz-4 h3 {
    margin-bottom: 12px;
}

.cb-quiz-4 h2 {
    line-height: 27px;
    margin-bottom: 26px;
}

.cb-quiz-4 p {
    line-height: 25px;
    margin-bottom: 30px;
}

.cb-button-container p {
    margin-bottom: 0;
}

@media only screen and (max-width: 1024px) {
    .cb-quiz-4 {
        flex-direction: column;
        margin: 28px auto 0;
        padding: 0 20px;
        width: auto;
    }

    .cb-col-1 {
        align-items: center;
    }

    .cb-image {
        height: 301px;
        width: 335.13px;
    }

    .cb-col-2 {
        width: 295px;
    }

    .cb-button-container {
        width: auto;
    }
}
</style>