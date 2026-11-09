<template>
  <!-- Показываем пагинацию только если страниц больше одной -->
  <div v-if="totalPages > 1" class="pagination flex items-center gap-2 py-8">
    
    <!-- Кнопка Назад -->
    <button
      @click="goToPage(currentPage - 1)"
      :disabled="currentPage === 1"
      class="btn btn-outline btn-sm"
      aria-label="Предыдущая страница"
    >
      Назад
    </button>

    <!-- Список страниц -->
    <nav aria-label="Пагинация страниц">
      <ul class="flex items-center gap-1">
        <li v-for="page in paginationRange" :key="page">
          <button
            v-if="isPageNumber(page)"
            @click="goToPage(page)"
            :class="{
              'btn btn-outline btn-sm': true,
              'btn-remove': page === currentPage,
              'text-gray-700 dark:text-gray-300 hover:bg-gray-100 dark:hover:bg-gray-700': page !== currentPage
            }"
            :aria-current="page === currentPage ? 'page' : undefined"
          >
            {{ page }}
          </button>
          <span
            v-else
            class="btn btn-outline  btn-sm"
          >
            ...
          </span>
        </li>
      </ul>
    </nav>

    <!-- Кнопка Вперед -->
    <button
      @click="goToPage(currentPage + 1)"
      :disabled="currentPage === totalPages"
      class="btn btn-outline  btn-sm"
      aria-label="Следующая страница"
    >
      Вперед
    </button>
  </div>
</template>

<script setup lang="ts">
import { computed } from 'vue'
import { useRoute, useRouter } from 'vue-router'

// Пропсы компонента
interface Props {
  /** Общее количество страниц */
  totalPages: number
  /** Имя параметра в URL (по умолчанию 'page') */
  paramName?: string
  /** Префикс пути (например, '/blog'). Если не задан, используется текущий путь */
  urlPrefix?: string
}

const props = withDefaults(defineProps<Props>(), {
  paramName: 'page',
  urlPrefix: undefined
})

const route = useRoute()
const router = useRouter()

// Вычисляем текущую страницу из URL. Если параметра нет, это первая страница.
const currentPage = computed(() => {
  const pageFromRoute = Number(route.params[props.paramName] || route.query[props.paramName])
  return isNaN(pageFromRoute) || pageFromRoute < 1 ? 1 : pageFromRoute
})

// Генерируем массив страниц для отображения (с троеточиями)
const paginationRange = computed(() => {
  const total = props.totalPages
  const current = currentPage.value
  
  if (total <= 7) {
    // Если страниц мало, показываем все
    return Array.from({ length: total }, (_, i) => i + 1)
  }

  const range: (number | 'dots')[] = []

  // Всегда показываем первую страницу
  range.push(1)

  if (current <= 4) {
    // Мы в начале: 1 2 3 4 5 ... 10
    range.push(2, 3, 4, 5)
    range.push('dots', total)
  } else if (current >= total - 3) {
    // Мы в конце: 1 ... 7 8 9 10
    range.push('dots', total - 4, total - 3, total - 2, total - 1)
    range.push(total)
  } else {
    // Мы в середине: 1 ... 5 6 7 ... 10
    range.push('dots', current - 1, current, current + 1, 'dots', total)
  }

  return range
})

// Проверяем, является ли элемент в массиве числом (для рендера ссылок)
const isPageNumber = (page: number | 'dots'): page is number => typeof page === 'number'

// Логика перехода
const goToPage = (page: number) => {
  if (page < 1 || page > props.totalPages || page === currentPage.value) return

  // Формируем путь
  const path = props.urlPrefix || route.path

  // Заменяем параметр в динамическом маршруте
  const params = { ...route.params }
  params[props.paramName] = page.toString()

  router.push({ path, query: {...params} })
  window.scrollTo({ top: 0, behavior: 'smooth' })
}

</script>