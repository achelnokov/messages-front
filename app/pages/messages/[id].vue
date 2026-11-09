<script setup>
import { ref, computed } from 'vue'

const fields = ref([
  { id: 'addressId', name: 'Идентификатор адреса', open: false },
  { id: 'cityId', name: 'Идентификатор города', open: false },
  { id: 'streetId', name: 'Идентификатор улицы', open: false },
])


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
          <label for="description"
            class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">Текст</label>
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
        <div class="mb-8 flex">
            <!-- Выпадающий список -->
            <div class="relative flex-1">
              <select class="w-full appearance-none px-3 py-2 pr-8 text-sm border border-gray-300 dark:border-gray-600 rounded-2 bg-white dark:bg-gray-700 text-gray-900 dark:text-white focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
                <option disabled selected>Выберите условие для добавления</option>
                <option v-for="item in availableToAdd" :key="item.id" :value="item.id">
                  {{ item.name }}
                </option>
              </select>
              <!-- Стрелочка кастомного селекта -->
              <div class="pointer-events-none absolute inset-y-0 right-0 flex items-center pr-2 text-gray-500 dark:text-gray-400">
                <Icon name="solar:arrow-down-line-duotone" size="16" />
              </div>
            </div>

            <!-- Кнопка Добавить -->
            <button 
              type="button"
              class="btn btn-primary btn-sm h-9 px-4 flex-shrink-0 ml-3"
            >
              <Icon name="solar:add-circle-bold" size="20" />
              Добавить
            </button>
     

        </div>


        <div class="block_params">
          <!-- Блок 1 -->
          <div v-for="field in fields"
            class="mb-3 px-4 border border-gray-200 dark:border-gray-700 rounded-lg bg-gray-50 dark:bg-gray-700">
            <div class="cursor-pointer py-2 relative"  @click="field.open = !field.open">
              <span>{{ field.name }}</span>
              <Icon name="solar:arrow-down-line-duotone" size="20" :class="{'absolute right-0': true, 'rotate-180': field.open}" />
            </div>
            <div :class="{'hidden': !field.open}">
              <div class="mb-3">
                <label class="block text-xs font-medium text-gray-600 dark:text-gray-400 mb-1">Название</label>
                <input type="text" :value="field.name" placeholder="То как поле будет выводиться в этой системе" class="w-full px-2 py-1.5 text-sm border border-gray-300 dark:border-gray-600 rounded 
                            bg-white dark:bg-gray-800 text-gray-900 dark:text-white focus:ring-1 focus:ring-blue-400">
              </div>
              <div class="mb-3">
                <label class="block text-xs font-medium text-gray-600 dark:text-gray-400 mb-1">Идентификатор</label>
                <input type="text" :value="field.id" placeholder="Исходных идентификатор поля в сторонней системе"
                  class="w-full px-2 py-1.5 text-sm border border-gray-300 dark:border-gray-600 rounded 
                            bg-white dark:bg-gray-800 text-gray-900 dark:text-white focus:ring-1 focus:ring-blue-400">

              </div>

              <button class="btn btn-primary mb-3 btn-sm h-9">
                <Icon name="solar:trash-bin-trash-bold" size="20" />
              </button>
            </div>
          </div>
        </div>

      </div>

    </div>
  </div>


</template>