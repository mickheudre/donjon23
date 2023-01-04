<template>
    <table class="table-auto">
        <thead>
            <tr>
                <th v-for="cells in this.block.children.results[0].table_row.cells"> {{ cells[0].plain_text }} </th>
            </tr>
        </thead>
        <tbody>
            
            <tr class="" v-for="(element, index) in this.block.children.results" :key="element.id">
                <td v-if="index > 0" v-for="cells in element.table_row.cells"> {{ cells[0].plain_text }} </td>
            </tr>
            
        </tbody>
    </table>
</template>

<script>

export default {
    name: 'Table',
    props: {
        block: Object
    }
}
</script>
