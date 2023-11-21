<template>
    <div class="cb-intro">
        <div class="cb-intro-col-1">
            <h1>Achieve Perfectly
                <span class="cb-italic">Smooth, Youthful</span> 
                Skin
            </h1>
            <p>Get a personalized skin care treatment </p>
        </div>
        <div class="cb-intro-col-2">
            <h2>Choose Your Goal</h2>
            <div @click="$emit('next')" class="cb-card">
                <h3>Remove Crepey Skin</h3>
                <img 
                    class="cb-card-display-image" 
                    src="../assets/images/intro/intro-crepey-skin-u.png" 
                    alt="Remove Crepey Skin"
                >
            </div>
            <div @click="$emit('next')" class="cb-card">
                <h3>Relieve Dry, Flaky Skin</h3>
                <img 
                    class="cb-card-display-image" 
                    src="../assets/images/intro/intro-dry-flaky.png" 
                    alt="Relieve Dry, Flaky Skin"
                >
            </div>
            <div @click="$emit('next')" class="cb-card">
                <h3>Get Firmer, Tighter, Younger <br> Looking Skin</h3>
                <img 
                    class="cb-card-display-image" 
                    src="../assets/images/intro/intro-firmer.png" 
                    alt="Get Firmer, Tighter, Younger Looking Skin"
                >
            </div>
        </div>
    </div>
</template>

<script>

export default {
    name: 'Intro',
}
</script>

<style scoped>
.cb-intro {
    display: flex;
    justify-content: center;
    gap: 161px;
    margin-top: 76px;
}

.cb-intro-col-1 {
    width: 430px;
    padding-left: 80px;
}

.cb-italic {
    font-style: italic;
}

.cb-intro-col-1 p {
    margin-top: 20px;
}

.cb-intro-col-2 h2 {
    margin-bottom: 34px;
}

.cb-card:active,
.cb-card:visited {
    border: 2px solid #E2C47C;
}

@media only screen and (max-width: 1024px) {
    .cb-intro {
        flex-direction: column;
        gap: 25px;
        margin-top: 22px;
        padding: 0 20px;
    }

    .cb-intro-col-1 {
        padding-left: 0;
        width: auto;
    }

    .cb-intro-col-1 h1 {
        width: 292px;
    }

    .cb-intro-col-1 p {
        margin-top: 15px;
    }

    .cb-card h3 {
        width: 55%;
    }
}
</style>