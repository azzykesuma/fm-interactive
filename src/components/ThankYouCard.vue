<script setup>
    const props = defineProps(['hideThankYou','selectedValue'])
</script>

<template>
    <div @click="props.hideThankYou" class="thankyou_card card_main">
        <img src="../assets/images/illustration-thank-you.svg" alt="thank-you-illustration">
        <div class="select_result">
            <p>You Selected {{ props.selectedValue }} out of 5</p>
        </div>
        <h2>Thank you!</h2>
        <p>
            We appreciate you taking the time to give a rating. if you ever need more support, 
            don't hesitate to get in touch!
        </p>
    </div>
</template>

<style lang="scss">
@import '../assets/base.scss';

    .thankyou_card {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;

        img {
            height: 80px;
            margin-bottom: 20px;
        }

        .select_result {
            background-color:$button-background-color;
            border-radius: 20px;
            padding: 15px;
            margin-bottom: 10px;
            
            p {
                font-size: 13px;
                color: $Orange;
                line-height: 0;
                transform: translateY(1px);
            }
        }

        p {
            text-align: center;
        }
    }
</style>