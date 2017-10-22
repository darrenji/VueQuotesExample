<template>
    <div class="container">
        <app-quote-grid :quotes="quotes"></app-quote-grid>
    </div>
</template>

<script>
    import QuoteGrid from './components/QuoteGrid.vue';
    export default {
        data: function(){
            return {
                maxQuotes: 10,
                quotes: ['Just a Quote Test']
            };
        },
        components: {
            appQuoteGrid: QuoteGrid
        }
    }
</script>

<style>

</style>
