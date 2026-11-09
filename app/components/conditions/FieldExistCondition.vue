<script setup>
defineProps({
  // Теперь принимаем объект с данными
  modelValue: {
    type: Object,
    required: true
  }
})

// Событие должно передавать весь обновленный объект
defineEmits(['update:modelValue', 'remove'])

// Названия полей (можно вынести в константу или пропс, если они динамические)
const fieldLabels = {
  length: 'Длина',
  width: 'Ширина',
  height: 'Высота'
}
</script>

<template>
  <div class="form-block border p-4 rounded bg-gray-50 dark:bg-gray-800">
    <h4 class="font-bold mb-2">Размеры (Числовые поля)</h4>

    <div v-for="(label, key) in fieldLabels" :key="key" class="mb-3">
      <label class="block text-xs font-medium text-gray-600 dark:text-gray-400 mb-1">{{ label }}</label>
      <input 
        :value="modelValue[key]"
        @input="$emit('update:modelValue', { ...modelValue, [key]: +$event.target.value })"
        type="number" 
        :placeholder="'Введите ' + label.toLowerCase()"
        class="w-full p-2 border border-gray-300 dark:border-gray-600 rounded bg-white dark:bg-gray-700"
      />
    </div>

    <button @click="$emit('remove')" class="mt-3 text-red-500 text-sm hover:underline">
      Удалить форму
    </button>
  </div>
</template>