<script setup>
    const systems = ref([
        { id: 1, name: 'OAO', description: 'Система оао' }, 
        { id: 2, name: 'ASRZ', description: 'Система ASRZ' }, 
        { id: 3, name: 'ForisFix', description: 'Система FF' }, 
    ])
</script>

<template>
    <div class="mb-4">
        <NuxtLink :to="{ name: 'systems-id', params: { id: 0 } }" class="btn btn-primary">
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
                        <th>Название</th>
                        <th>Описание</th>
                        <th class="!text-right">Действия</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="system in systems">
                        <td>{{system.id}}</td>
                        <td>{{system.name}}</td>
                        <td>{{system.description}}</td>
                        <td>
                            <div class="flex gap-3 justify-end">
                                <NuxtLink :to="{ name: 'systems-id', params: { id: system.id } }" class="btn btn-outline btn-icon btn-sm">
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