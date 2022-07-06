<template>
<div class="container" :class="product.outOfStock && 'out-of-stock'">
    <div>
        <h4>{{product.title}}</h4>
        <p class="pledge">Pledge ${{product.pledge}} or more</p>
    </div>
    
    <p class="descr">{{ product.descr }}</p>

    <div>
        <div class="remaining"><span>{{product.remaining}}</span> left</div>
        <button class="btn" :data-option="product.title" @click="$emit('openPledge', $event.target.dataset.option)">
            <slot name="button">Select Reward</slot>
        </button>
    </div>
</div>
</template>

<script>
    export default{
        name:'ProductCard',
        props:['product'],
        emits:['openPledge'],
    }
</script>

<style scoped>

.container{
    border:0.01rem solid var(--dark-gray);
    border-radius:0.6rem;
    padding:1.3rem;
    margin-bottom:1.3rem;
}

h4{
    color:var(--black);
    font-size: 14px;
}

.pledge{
    color:var(--mod-cyan);
    font-weight: 500;
    margin-top:0.8rem;
}

.descr{
    padding:1.5rem 0;
    line-height: 1.5rem;
}

.remaining{
    padding-bottom: 1.5rem;
}
.remaining>span{
    color:var(--black);
    font-size: 1.8rem;
    font-weight: 700;
    margin-right: 0.5rem;
}

@media (min-width:1025px){
.container >div{
    display:flex;
    justify-content: space-between;
}

.pledge{
    margin:0;
}
.remaining{
    padding:0;
}
}
</style>