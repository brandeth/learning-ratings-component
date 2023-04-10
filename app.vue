<script lang="ts" setup>
const selectedOption = ref<number | null>(null);

const handleSelect = (value: number) => {
  selectedOption.value === value 
    ? (selectedOption.value = null) 
    : (selectedOption.value = value);
}
</script>

<template>
  <div class="main">
    <div class="rating">
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

      <Button rounded type="orange" class="rating-submit">Submit</Button>
    </div>
  </div>
</template>
