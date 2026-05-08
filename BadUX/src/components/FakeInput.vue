<!-- FakeInput.vue -->

<script setup>
import { computed, ref } from 'vue'

const props = defineProps({
  modelValue: {
    type: String,
    default: ''
  },

  placeholder: {
    type: String,
    default: 'Eingeben...'
  },

  type: {
    type: String,
    default: 'text'
  }
})

const emit = defineEmits(['update:modelValue'])

const inputRef = ref(null)

function focusInput() {
  inputRef.value?.focus()
}

const displayValue = computed(() => {
  if (props.type === 'password') {
    return props.modelValue
      ? '•'.repeat(props.modelValue.length)
      : props.placeholder
  }

  return props.modelValue || props.placeholder
})
</script>

<template>
  <div class="input-wrapper" @click="focusInput">
    <div
      class="fake-input"
      :class="{ placeholder: !modelValue }"
    >
      {{ displayValue }}
    </div>
    <input
      ref="inputRef"
      :type="type"
      class="real-input"
      :value="modelValue"
      @input="emit('update:modelValue', $event.target.value)"
    />
  </div>
</template>

<style scoped>
.input-wrapper {
  position: relative;
  width: 320px;
  cursor: text;
  writing-mode: vertical-rl;
}

.fake-input {
  padding: 14px;
  border-radius: 12px;
  border: 2px solid #444;
  background: #1a1a1a;
  color: white;
  font-size: 16px;
  transition: 0.2s;
  writing-mode: vertical-rl;
}

.fake-input.placeholder {
  color: #777;
  writing-mode: vertical-rl;
}

.input-wrapper:hover .fake-input {
  border-color: #888;
}

.real-input {
  position: absolute;
  inset: 0;

  width: 100%;
  height: 100%;

  opacity: 0;

  border: none;
  outline: none;
  writing-mode: vertical-r;
}
</style>