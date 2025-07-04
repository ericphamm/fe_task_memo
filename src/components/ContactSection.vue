<template>
  <section id="contact"
    class="relative min-h-screen w-full bg-cover bg-center text-white md:flex items-center justify-center overflow-x-hidden"
    :style="{ backgroundImage: `url(${contactBg})` }" style="touch-action: manipulation;">
    <div class="absolute inset-0 bg-[#2F1893] opacity-40 z-0"></div>

    <div class="relative z-10 max-w-7xl mx-auto py-20 px-6">
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-16 items-center">
        <!-- left side -->
        <div>
          <h3 class="text-white text-4xl md:text-[42px] font-bold tracking-[-0.4px]">
            Let’s Keep in Touch
          </h3>
          <p class="text-[22px] font-medium mt-6 mb-14">
            We have created a new product that will help designers, developers
            and companies create websites for their startups quickly and easily.
          </p>

          <!-- contact -->
          <div class="space-y-8">
            <div class="flex items-center space-x-4">
              <div>
                <font-awesome-icon :icon="['fas', 'phone']" class="text-white text-[18px]" />
              </div>
              <p class="text-white text-base font-normal">+1 555 505 5050</p>
            </div>

            <div class="flex items-center space-x-4">
              <div>
                <font-awesome-icon :icon="['fas', 'envelope']" class="text-white text-[18px]" />
              </div>
              <p class="text-white text-base font-normal">
                info@designmodo.com
              </p>
            </div>

            <div class="flex items-start space-x-4">
              <div>
                <font-awesome-icon :icon="['far', 'building']" class="text-white text-[18px]" />
              </div>
              <div>
                <p class="text-white text-base font-normal">
                  San Francisco, CA560 Bush St & <br />
                  20th Ave, Apt5 San Francisco,<br />
                  230909
                </p>
              </div>
            </div>
          </div>
        </div>

        <!-- contact form -->
        <div class="bg-white rounded-[10px] px-12 py-20">
          <form @submit.prevent="submitForm" class="space-y-6">
            <div class="grid grid-cols-1 md:grid-cols-5 gap-6">
              <div class="md:col-span-3">
                <label for="name" class="block text-sm font-bold mb-2 uppercase tracking-wider text-[#1E0E62]">Your
                  Name</label>
                <input id="name" v-model="form.name" type="text"
                  :class="['input-field', errors.name && 'border-red-500']" class="input-field"
                  placeholder="First name" />
                <p v-if="errors.name" class="text-red-500 text-sm mt-1">
                  {{ errors.name }}
                </p>
              </div>
              <!-- budget -->
              <div class="md:col-span-2">
                <label for="budget"
                  class="block text-sm font-bold mb-2 uppercase tracking-wider text-[#1E0E62]">Budget</label>
                <div class="relative">
                  <select id="budget" v-model="form.budget"
                    class="w-full h-[50px] appearance-none bg-white border-2 border-gray-200 rounded-full px-6 text-xl font-light text-[#1E0E62] focus:outline-none focus:border-[#25DAC5] cursor-pointer pr-12">
                    <option v-for="option in budgetOptions" :key="option" :value="option">
                      {{ option }}
                    </option>
                  </select>
                  <div class="pointer-events-none absolute inset-y-0 right-4 flex items-center">
                    <img src="/src/assets/images/arrow-down.svg" alt="Arrow Down" class="w-3 h-3 mt-[1px]" />
                  </div>
                </div>
              </div>
            </div>
            <!-- email -->
            <div>
              <label for="email" class="block text-sm font-bold mb-2 uppercase tracking-wider text-[#1E0E62]">Input
                Field</label>
              <input id="email" v-model="form.email" type="text"
                :class="['input-field', errors.email && 'border-red-500']" class="input-field"
                placeholder="name@mail.com" />
              <p v-if="errors.email" class="text-red-500 text-sm mt-1">
                {{ errors.email }}
              </p>
            </div>
            <!-- message -->
            <div>
              <label for="message" class="block text-sm font-bold mb-2 uppercase tracking-wider text-[#1E0E62]">Your
                Message</label>
              <textarea id="message" v-model="form.message" rows="4" :class="[
                'input-field resize-none h-[110px] rounded-[10px]',
                errors.message && 'border-red-500',
              ]" class="input-field resize-none h-[110px] rounded-[10px]" placeholder="Message" />
              <p v-if="errors.message" class="text-red-500 text-sm mt-1">
                {{ errors.message }}
              </p>
            </div>
            <div class="flex items-center justify-between">
              <!-- sendcopy-->
              <div>
                <label class="flex items-center cursor-pointer">
                  <input type="checkbox" class="hidden" id="sendCopy" v-model="sendCopy" />
                  <div class="w-5 h-5 rounded-md border-2 flex items-center justify-center transition-all" :class="sendCopy
                      ? 'bg-[#25DAC5] border-[#25DAC5]'
                      : 'border-gray-300'
                    ">
                    <Check class="w-4 h-4 text-[#1E0E62] transition-opacity duration-200"
                      :class="sendCopy ? 'opacity-100' : 'opacity-0'" />
                  </div>
                  <span class="ml-2 font-normal text-base text-[#15143966]">
                    Send me a copy
                  </span>
                </label>
              </div>
              <!-- send button -->
              <button type="submit"
                class="px-8 md:w-[120px] h-[50px] bg-[#25DAC5] text-white text-[18px] font-medium rounded-full flex items-center justify-center transition-all duration-300 transform hover:scale-105 hover:bg-[#00e69a]">
                Send
              </button>
            </div>
            <!-- success message -->
            <div v-if="showSuccess"
              class="bg-green-100 border border-green-400 text-green-700 px-4 py-3 rounded-full mt-4">
              <p>Your message has been sent successfully!</p>
            </div>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import contactBg from "@/assets/images/contact_bg.jpg";
import { ref } from "vue";
import { Check } from "lucide-vue-next";
const sendCopy = ref(false);
const showSuccess = ref(false);
const showError = ref(false);

const budgetOptions = ["$500", "$1,000", "$2,000", "$4,000", "$10,000+"];

const form = ref({
  name: "",
  email: "",
  budget: "$500",
  message: "",
});

const errors = ref({
  name: "",
  email: "",
  message: "",
});

function submitForm() {
  const { name, email, message } = form.value;

  errors.value = { name: "", email: "", message: "" };
  showError.value = false;

  let isValid = true;

  if (!name.trim()) {
    errors.value.name = "Please enter your name.";
    isValid = false;
  }

  if (!email.trim()) {
    errors.value.email = "Please enter your email address.";
    isValid = false;
  } else {
    const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    if (!emailPattern.test(email)) {
      errors.value.email = "Please enter a valid email.";
      isValid = false;
    }
  }

  if (!message.trim()) {
    errors.value.message = "Please enter your message.";
    isValid = false;
  }

  if (!isValid) {
    showError.value = true;
    return;
  }

  showSuccess.value = true;
  form.value = { name: "", email: "", budget: "$500", message: "" };
  sendCopy.value = false;

  setTimeout(() => (showSuccess.value = false), 4000);
}
</script>
