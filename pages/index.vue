<template>
   <div class="form-container">
    <Transition name="slide" mode="out-in">
      <component
        :is="currentComponent"
        :formData="formData"
        @next="nextStep"
        @prev="prevStep"
        @submit="submitForm"
      />
    </Transition>
  </div>
</template>

<script setup>
import StepOne from '~/components/StepOne.vue'
import StepTwo from '~/components/StepTwo.vue'
import StepThree from '~/components/StepThree.vue'

const step = ref(1)

const formData = reactive({
  name: '',
  email: '',
  age: '',
  address: ''
})

/* Load from localStorage */
onMounted(() => {
  const saved = localStorage.getItem('multiForm')
  if (saved) Object.assign(formData, JSON.parse(saved))
})

/* Save to localStorage whenever data changes */
watch(
  formData,
  (val) => {
    localStorage.setItem('multiForm', JSON.stringify(val))
  },
  { deep: true }
)

const components = {
  1: StepOne,
  2: StepTwo,
  3: StepThree
}

const currentComponent = computed(() => components[step.value])

const nextStep = () => {
  if(step.value === 1 && formData.name && formData.email) {
    const regex = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
    if (!regex.test(formData.email)) {
      alert('Please enter a valid email address!')
    } else {
      step.value++
    }
  }
  else if(step.value === 2 && formData.age) step.value++
  else alert('Please fill the age fields!')
}

const prevStep = () => {
  if (step.value > 1) step.value--
}

const submitForm = () => {
  console.log('Final Data:', formData)
  localStorage.removeItem('multiForm')
  if( step.value === 3 && formData.address ) {
    alert('Form submitted!') 
  }
  else {alert('Please fill the address fields!')}
}
</script>

<style scoped>
.form-container {
  width: 400px;
  margin: auto;
}

/* Slide animation */
.slide-enter-active,
.slide-leave-active {
  transition: all 0.4s ease;
}
.slide-enter-from {
  transform: translateX(100%);
  opacity: 0;
}
.slide-leave-to {
  transform: translateX(-100%);
  opacity: 0;
}
</style>
