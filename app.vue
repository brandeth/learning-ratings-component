<script lang="ts" setup>
const isSubmitted = ref(false);
const selectedOption = ref<number | null>(null);

const ratingSubmitted = computed(() => selectedOption.value !== null && isSubmitted.value);

const handleSelect = (value: number) => {
  selectedOption.value === value 
    ? (selectedOption.value = null) 
    : (selectedOption.value = value);
}

const handleSubmit = () => {
  isSubmitted.value = true;

  setTimeout(() => {
    isSubmitted.value = false;
    selectedOption.value = null;
  }, 3000);
}
</script>

<template>
  <div class="main">
    <div class="rating">
      <div v-if="!ratingSubmitted" class="rating-body">
        <div class="icon">
          <RoundContainer>
            <img src="@/assets/images/icon-star.svg" alt="Vue.js" />
          </RoundContainer>
        </div>

        <h1 class="rating-title">How did we do?</h1>

        <p class="rating-body">Please let us know how we did with your support request. All feedback is appreciated to help us improve our offering.</p>

        <div class="rating-options">
          <RoundContainer :class="{ 'selected': i === selectedOption }" class="cursor-pointer rating-option" v-for="i in 5" :key="i" @click="handleSelect(i)">
            {{ i }}
          </RoundContainer>
        </div>

        <Button @click="handleSubmit" rounded type="orange" class="rating-submit">Submit</Button>
      </div>

      <div v-else class="rating-thank-you">
        <div>
          <img src="@/assets/images/illustration-thank-you.svg" alt="Vue.js" />
        </div>

        <p class="rating-selected">You selected {{ selectedOption }} out of 5</p>

        <h1 class="rating-thank-you-title">Thank you!</h1>

        <p class="rating-thank-you-body">We appreciate you taking the time to give a rating. If you ever need more support, don't hesitate to get in touch!</p>
      </div>
    </div>
  </div>
</template>
