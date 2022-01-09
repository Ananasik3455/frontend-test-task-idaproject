<template>
    <header>
        <h2>Добавление товара</h2>
        <div class="select_search">
            <select @change="$emit('sorting', selected)"  v-model="selected" name="sorting" id="sort-selector">
                <option
                    v-for="option in options"
                    :key="option.value"
                    :value="option.value"
                >
                {{option.text}}
                </option>
            </select>
        </div>
    </header>
</template>

<script>
export default {
    data: () => ({
        options: [
            {
                value: 'default',
                text: 'По умолчанию'
            },
            {
                value: 'higher',
                  text: 'Цена ↑',
            },
            {
                value: 'lower',
                text: 'Цена ↓',
            },
            {
                value: 'byName',
                text: 'По алфавиту',
            },
        ],
        selected: 'default'
    })
}
</script>
