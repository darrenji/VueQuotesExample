<template>
    <div class="container">
     <div class="row text-center">
         <img src="./assets/us.jpg" class="img-circle" style="height:250px;margin-top:20px;" alt="">
     </div>
      <div class="row text-center">
          <h3>今天有{{maxQuotes}}项作业</h3>
      </div>
       <app-header :dynamicWidth="dynamicWidthObject" :quoteCount="maxQuotes-quotes.length" :maxQuotes="maxQuotes"></app-header>
    
       <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
<!--
       <div class="row">
           <div class="col-sm-12 text-center">
               <div class="alert alert-info">
              
               </div>
           </div>
       </div>
-->
       <section v-if="isShowAdd==true">
           <app-new-quote @quoteAdded="newQuote" @reset="reset" @ok="ok"></app-new-quote>
       </section>
       <section v-else>
           <div class="text-center">
               <button class="btn btn-primary" @click="isShowAdd=true">我还有其它作业</button>
           </div>
       </section>
    </div>
</template>

<script>
    import QuoteGrid from './components/QuoteGrid.vue';
    import NewQuote from './components/NewQuote.vue';
    import Header from './components/Header.vue';
    export default {
        data: function(){
            return {
                maxQuotes: 0,
                quotes: [],
                isShowAdd: true
            };
        },
        computed:{
            dynamicWidthObject : function(){
                
                if(this.maxQuotes == 0 || this.quotes.length == this.maxQuotes){
                    return {width:0 + '%'};
                }
                return {
                   width:  (1-(this.quotes.length/this.maxQuotes))*100 + '%'
                    //width: '30%'
                };
            }
        },
        methods:{
            newQuote(quote){
                this.quotes.push(quote);
                this.maxQuotes = this.quotes.length;
            },
            deleteQuote(index){
                this.quotes.splice(index, 1);
                if(this.quotes.length == 0){
                    this.maxQuotes = 0;
                    
                    setTimeout(function(){
                        return alert('恭喜作业完成了');
                    }, 1000);
                    
                }
            },
            setInitialMessage(){
                if(this.quotes.length==0){
                    this.msg = '添加今天的作业吧^_^';
                }
            },
            reset() {
                this.quotes = [];
                this.maxQuotes = 0;
            },
            ok(){
                this.isShowAdd = false;
                this.maxQuotes = this.quotes.length;
            }
        },
        components: {
            appQuoteGrid: QuoteGrid,
            appNewQuote: NewQuote,
            appHeader: Header
        }

    }
</script>

<style>

</style>
