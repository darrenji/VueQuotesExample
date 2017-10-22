<template>
    <div class="row">
       <div class="col-sm-12">
            <div class="progress">
                <div class="progress">
                    <div class="progress-bar" role="progressbar" aria-valuemin="0" aria-valuemax="100"
                       :style="dynamicWidth">
                        {{ quoteCount }}/{{ maxQuotes }}
                    </div>
                </div>
            </div>
       </div>     
    </div>
</template>


<script>
    export default {
        props: ['dynamicWidth', 'quoteCount','maxQuotes']
    }
</script>