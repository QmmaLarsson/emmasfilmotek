<script>
export default {
    props: {
        movie: Object
    }
}
</script>

<template>
    <div class="px-4">
        <table class="min-w-full border border-red-600 mb-8">
            <thead class="bg-red-600 text-white">
                <tr>
                    <th colspan="2">{{ movie.name }}</th>
                </tr>
            </thead>
            <tbody>
                <tr class="border-b border-red-600">
                    <td class="px-4 py-2">År</td>
                    <td class="px-4 py-2">{{ movie.year }}</td>
                </tr>
                <tr class="border-b border-red-600">
                    <td class="px-4 py-2">Tittad på</td>
                    <td class="px-4 py-2">{{ movie.completed ? "Ja" : "Nej" }}</td>
                </tr>
                <tr>
                    <td colspan="2" class="text-center"><button
                            class="bg-red-600 text-white font-bold py-2 px-4 m-2 rounded min-w-[110px] transition-all duration-300 ease-in-out hover:scale-105">Ta
                            bort</button></td>
                </tr>
            </tbody>
        </table>
    </div>
</template>