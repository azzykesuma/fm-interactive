<script setup>
  import { ref } from 'vue';
  import ThankYouCard from './components/ThankYouCard.vue';
  const buttonValue = [1,2,3,4,5];
  const showThankYou = ref(false);
  const selectedValue = ref('');
  const showError =  ref(false)
  const handleSubmit = () => {
    if(selectedValue.value !== '') {
      showThankYou.value = true;
    } else {
      showError.value = true;
    }
  }
  const hideThankYou = () => {
    showThankYou.value = false
    selectedValue.value = ''
  }
  const handleClick = btn => {
    selectedValue.value = btn
    showError.value = false
  }
</script>

<template>
  <div v-if="!showThankYou" class="card_main">
    <div class="icon_container">
      <img src="./assets/images/icon-star.svg" alt="icon-start">
    </div>
    <h2>How Did we do?</h2>
    <p>Please let us know how we did with your support request. All feedback is appreciated to help us improve our offering</p>
    <div class="button_container">
      <button @click="handleClick(btn)" v-for="(btn,index) in buttonValue" :key="index">{{ btn }}</button>
    </div>
    <button @click="handleSubmit" class="submit">Submit</button>
    <p class="errorText" v-if="showError">Please select number 1 - 5</p>
  </div>
  <ThankYouCard :selectedValue="selectedValue" :hideThankYou="hideThankYou" v-if="showThankYou"/>
</template>

<style lang="scss">
@import './assets/base.scss';
 .card_main {
    color: $White;
    background-color: $Dark-Blue;
    padding: 20px;
    margin: 20px;
    border-radius: 20px;
    max-width: 400px;

    .icon_container {
      background-color: $button-background-color;
      border-radius: 50%;
      padding: 10px;
      width: 40px;
      height: 40px;
      display: flex;
      align-items: center;
      justify-content: center;
      margin-bottom: 20px;

      img {
        height: 15px;
      }
    }
    h2 {
      margin-bottom: 10px;
      font-weight: 700;
    }
    p {
      font-weight: 400;
      opacity: .7;
      font-size: 14px;
      line-height: 1.5;
    }
    .button_container {
      margin-block: 20px;
      display: flex;
      justify-content: space-between;

      button {
        background-color: $button-background-color;
        color: white;
        padding: 10px;
        border: none;
        cursor: pointer;
        border-radius: 50%;
        width: 40px;
        height: 40px;
        transition: background-color .3s ease-in-out;

        &:hover {
          background-color: $Medium-Grey;
        }
        &:focus {
          background-color: $Orange;
        }

        @media screen and (min-width: 740px) {
          width: 50px;
          height: 50px;
        }
      }
    }
    .submit {
      width: 100%;
      padding: 13px;
      background-color: $Orange;
      border-radius: 20px;
      border: none;
      cursor: pointer;
      color: $White;
      text-transform: uppercase;
      letter-spacing: 3px;
      margin-bottom: 10px;
    }

    .errorText {
      color: red;
      text-align: center;
    }
  }
</style>