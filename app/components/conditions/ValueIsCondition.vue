<script setup>
import { ref } from 'vue'
defineProps({
  modelValue: {
    type: Object,
    required: true
  }
})
defineEmits(['update:modelValue', 'remove'])
let open = ref(false)

const fieldLabels = {
  length: 'Длина',
  width: 'Ширина',
  height: 'Высота'
}
</script>

<template>
  <div 
    class="mb-3 px-4 border border-gray-200 dark:border-gray-700 rounded-xs bg-gray-50 dark:bg-gray-700">
    <div class="cursor-pointer py-2 relative" @click="open = !open">
      <span>Значение параметра один из</span>
      <Icon name="solar:arrow-down-line-duotone" size="20"
        :class="{ 'absolute right-0 transition-all': true, 'rotate-180': open }" />
    </div>
    <div
      :class="{ 'max-h-0 opacity-0': !open, 'max-h-96 opacity-100': open, 'overflow-hidden transition-all duration-300 ease-in-out': true }">
      <div class="mb-3">

        <label class="block text-xs font-medium text-gray-600 dark:text-gray-400 mb-1">Идентификатор</label>
        <input type="text" value="" placeholder="Исходных идентификатор поля в сторонней системе" class="w-full px-2 py-1.5 text-sm border border-gray-300 dark:border-gray-600 rounded 
                            bg-white dark:bg-gray-800 text-gray-900 dark:text-white focus:ring-0 focus:ring-blue-500 focus:border-blue-500 focus:outline-none">
      </div>

      <div class="mb-3">
        <label class="block text-xs font-medium text-gray-600 dark:text-gray-400 mb-1">Название</label>
        <input type="text" value="" placeholder="То как поле будет выводиться в этой системе" class="w-full px-2 py-1.5 text-sm border border-gray-300 dark:border-gray-600 rounded 
                            bg-white dark:bg-gray-800 text-gray-900 dark:text-white focus:ring-0 focus:ring-blue-500 focus:border-blue-500 focus:outline-none">
      </div>


      <button class="btn btn-primary mb-3 btn-sm h-9" @click="$emit('remove')">
        <Icon name="solar:trash-bin-trash-bold" size="20" />
      </button>
    </div>
  </div>
</template>