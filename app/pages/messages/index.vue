<script setup>
    const messages = ref([
        { id: 1, title: 'Сообщение для Москвы', description: 'Система оао', enabled: true }, 
        { id: 2, title: 'Новый год 2027', description: 'Напоминание о поздравлении с НГ 2027', enabled: false }, 
        { id: 3, title: 'Спец тарифы', description: 'Оповещение о спец тарифах для новых ЖК', enabled: true }, 
        { id: 3, title: 'Отключение функционала', description: 'Информация об отключении продажи 2PON', enabled: true }, 
    ])
</script>

<template>
    <div class="mb-4">
        <NuxtLink :to="{ name: 'messages-id', params: { id: 0 } }" class="btn btn-primary">
            <Icon name="solar:add-circle-bold" size="20" />
            Создать
        </NuxtLink>
    </div>
    <div class="card">

        <div class="table-wrap">
            <table>
                <thead>
                    <tr>
                        <th>ID</th>
                        <th>Наименование</th>
                        <th>Вкл/Выкл</th>
                        <th>Описание</th>
                        <th class="!text-right">Действия</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="message in messages">
                        <td>{{message.id}}</td>
                        <td>{{message.title}}</td>
                        <td><span :class="message.enabled == true ? 'badge-pill badge-active' : 'badge-pill badge-inactive'">{{message.enabled == true ? 'Включен' : 'Выключен'}}</span></td>
                        <td>{{message.description}}</td>
                        <td>
                            <div class="flex gap-3 justify-end">
                                <NuxtLink :to="{ name: 'messages-id', params: { id: message.id } }" class="btn btn-outline btn-icon btn-sm">
                                    <Icon name="solar:pen-bold" size="15" />
                                </NuxtLink >

                                <button class="btn btn-remove btn-icon btn-sm">
                                    <Icon name="solar:trash-bin-trash-bold" size="15" />
                                </button>
                            </div>
                        </td>
                    </tr>

                </tbody>
            </table>
        </div>


        <div>
            <Pagination :totalPages="6" />
        </div>
    </div>
</template>