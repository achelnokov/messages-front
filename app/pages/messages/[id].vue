<script setup>
import { ref } from 'vue'

import FieldExistCondition from '~/components/conditions/FieldExistCondition.vue'
import ValueIsCondition from '~/components/conditions/ValueIsCondition.vue'

const availableToAdd = ref([
  { id: 'fieldExist', name: 'Наличие параметра', component: FieldExistCondition, desc: 'true - если в запросе сообщений есть указанное поле, в остальных false' },
  { id: 'valueIs', name: 'Значение параметра одно из', component: ValueIsCondition, desc: 'true - если одно из значений указанного параметра совпадает, в остальном false' }
])

const conditionInfo = ref('')
const dynamicForms = ref([])

const selectedField = ref('')

const addConditionForm = (data) => {
  if (selectedField.value == '') {
    return 
  }

  dynamicForms.value.push({
    id: crypto.randomUUID(),
    type: selectedField.value,
    data: '' // Начальные данные формы
  })
  selectedField.value = ''
  conditionInfo.value = ''
}

const removeForm = (formId) => {
  dynamicForms.value = dynamicForms.value.filter(f => f.id !== formId)
}

const updateFormData = (formId, newValue) => {
  const index = dynamicForms.value.findIndex(f => f.id === formId)
  if (index !== -1) {
    dynamicForms.value[index].data = newValue
  }
}

const changeConditionSelect = (event) => {
  conditionInfo.value = ''
  const value = event.target.value;
  availableToAdd.value.forEach(element => {
    if (element.id == value) {
      conditionInfo.value = element.desc
    }
  });
}
</script>

<template>
  <div class="card">


    <!-- Грид-контейнер: 2 колонки на десктопе, 1 на мобильных -->
    <div class="grid grid-cols-1 lg:grid-cols-2 gap-0">

      <!-- ЛЕВАЯ ЧАСТЬ: Основные поля -->
      <div class="p-8 lg:pr-6 lg:border-r border-gray-200 dark:border-gray-700">

        <h2 class="text-2xl font-bold mb-2">Настройки сообщения</h2>

        <!-- Поле Название -->
        <div class="mb-4">
          <label for="name" class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">Название</label>
          <input type="text" id="name" name="name" placeholder="Введите название сообщения" class="w-full px-4 py-2.5 border border-gray-300 dark:border-gray-600 rounded-lg 
                        bg-white dark:bg-neutral-900 text-gray-900 dark:text-white 
                        focus:ring-2 focus:ring-blue-500 focus:border-blue-500 
                        focus:outline-none transition-shadow">
        </div>

        <!-- Поле Описание -->
        <div class="mb-4">
          <label for="description" class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">Текст</label>
          <textarea id="description" name="description" rows="3" placeholder="Текст сообщения" class="w-full px-4 py-2.5 border border-gray-300 dark:border-gray-600 rounded-lg 
                           bg-white dark:bg-neutral-900 text-gray-900 dark:text-white 
                           focus:ring-2 focus:ring-blue-500 focus:border-blue-500 
                           focus:outline-none transition-shadow resize-none"></textarea>
        </div>



        <button class="btn btn-primary mb-3 h-9">
          <Icon name="solar:diskette-bold-duotone" size="20" />
          Сохранить
        </button>
      </div>

      <!-- ПРАВАЯ ЧАСТЬ: Маленькие блоки -->
      <div class="p-8 lg:pl-6">
        <div class="flex justify-between">
          <h2 class="text-2xl font-bold text-gray-900 dark:text-white mb-9  ">Условия</h2>
        </div>


        <!-- НОВЫЙ БЛОК: Группа добавления -->
        <div class="mb-4 flex">
          <!-- Выпадающий список -->
          <div class="relative flex-1">
            <select @change="changeConditionSelect" v-model="selectedField"
              class="w-full appearance-none px-3 py-2 pr-8 text-sm border border-gray-300 dark:border-gray-600 rounded-xs bg-white dark:bg-gray-700 text-gray-900 dark:text-white focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
              <option value="">Выберите условие из списка</option>
              <option v-for="item in availableToAdd" :key="item.id" :value="item.id">
                {{ item.name }}
              </option>
            </select>
            <!-- Стрелочка кастомного селекта -->
            <div
              class="pointer-events-none absolute inset-y-0 right-0 flex items-center pr-2 text-gray-500 dark:text-gray-400">
              <Icon name="solar:arrow-down-line-duotone" size="16" />
            </div>
          </div>

          <!-- Кнопка Добавить -->
          <button @click="addConditionForm('')" type="button"
            class="btn btn-primary btn-sm h-9 px-4 flex-shrink-0 ml-3">
            <Icon name="solar:add-circle-bold" size="20" />
            Добавить
          </button>


        </div>

        <div v-if="conditionInfo != ''" class="badge-active p-3 rounded-xs">{{ conditionInfo }}</div>

        <div class="conditions">
          <component v-for="form in dynamicForms" :key="form.id"
            :is="availableToAdd.find(f => f.id === form.type)?.component" :model-value="form.data"
            @update:modelValue="(val) => updateFormData(form.id, val)" @remove="removeForm(form.id)" />
        </div>



        <!-- -->


      </div>

    </div>
  </div>


</template>