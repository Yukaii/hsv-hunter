<template>
  <div :class="className" @click="onClose">
    <div
      class="z-50 flex max-h-[80%] w-[90%] max-w-xs flex-col space-y-4 overflow-auto rounded-md bg-[#1f2937] p-4"
      @click.stop
    >
      <slot />
    </div>
  </div>
</template>

<script setup>
import { cn } from '../utils/index'

const props = defineProps({
  isOpen: Boolean,
  modalClass: {
    type: String,
    default: '',
  },
})

const className = computed(() => {
  return cn(
    'fixed left-0 top-0 z-50 flex size-full items-center justify-center bg-black/50',
    props.modalClass,
    !props.isOpen && 'hidden'
  )
})

const emit = defineEmits(['onClose'])
const onClose = () => {
  emit('onClose')
}
</script>
