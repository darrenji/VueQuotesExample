<template>
    <div class="row">
       <form>
           <div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3 form-group">
                <textarea rows="3" class="form-control" v-model="quote"></textarea>
            </div>
            <div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3 form-group">
                <button class="btn btn-primary" @click.prevent="createNew">添加作业</button>
                <button class="btn btn-default" @click.prevent="reset">重新来</button>
                <button class="btn btn-danger" @click.prevent="ok">好，就这么多作业了</button>
            </div>
            
       </form>
        
    </div>
</template>


<script>
    export default {
        data: function(){
            return {
                quote: ''
            };
        },
        methods: {
            createNew(){
                //广播出去
                this.$emit('quoteAdded', this.quote);
                this.quote = '';
            },
            reset(){
                this.$emit('reset');
            },
            ok(){
                this.$emit('ok');
            }
        }
    }
</script>


<style>

</style>