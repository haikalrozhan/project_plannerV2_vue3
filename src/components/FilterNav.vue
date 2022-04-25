<template>
<div class="filter-nav">
  <button @click="filterChange('all')" :class="{active: current === 'all'}">View All</button>
  <button @click="filterChange('ongoing')" :class="{active: current === 'ongoing'}">Ongoing</button>
  <button @click="filterChange('complete')" :class="{active: current === 'complete'}">Complete</button>
</div>
  
</template>

<script>
export default {
    props: ['current'],
    methods: {
        filterChange(by){
            this.$emit('filter', by)
        }
    }
}
</script>

<style>
.filter-nav{
    margin-bottom: 20px;
    
}
.filter-nav button{
   border: none;
   padding: 10px;
}
.filter-nav .active{
    background: aquamarine;
}
</style>