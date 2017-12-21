<template>
  <div class="container">
    <app-header :maxQuotes="maxQuotes" :quoteCount="quotes.length"></app-header>
    <new-quote @quoteAdded="newQuote"></new-quote>
    <quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></quote-grid>
    <div class="row">
      <div class="col-sm-12 text-center">
        <div class="alert alert-info">Info: Click on the quote to delete it!</div>
      </div>
    </div>
  </div>
</template>

<script>

  import QuoteGrid from './components/QuoteGrid.vue'
  import NewQuote from './components/NewQuote.vue'
  import Header from './components/Header.vue'

  export default {
    name: 'app',
    data () {
      return {
        maxQuotes: 10,
        quotes: [
          'Just a single quote'
        ]
      }
    },
    components: {
      'quote-grid': QuoteGrid,
      'new-quote': NewQuote,
      'app-header': Header
    },

    methods:{
      newQuote(quote){
        if (this.quotes.length >= this.maxQuotes) {
          return alert('delete first')
        }
        this.quotes.push(quote)
      },
      deleteQuote(index){
        this.quotes.splice(index, 1)
      }
    }
  }

</script>

<style lang="scss">

</style>
