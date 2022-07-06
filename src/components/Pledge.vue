<template>
    <div class="container" v-for="product in products" :key="product.title" :class="product.outOfStock && 'out-of-stock'">
        <div>
            <div>
                <input type="radio" :id="product.title" name="products" :value="product.title" @change="$emit('update:modelValue',$event.target.value)" :checked="option==product.title" :disabled="product.outOfStock">
                <pre>{{checked}}</pre>
                <label :for="product.title">
                    <div>
                        <h4>{{product.title}}</h4>
                        <div class="pledge" v-if="product.pledge">Pleadge with ${{ product.pledge }} or more</div>
                    </div>
                </label>
            </div>
            <div class="descr">
                {{product.descr}}
            </div>
            <div class="remaining" v-if="product.remaining"><span>{{ product.remaining }}</span> left</div>
        </div>
        <div class="action" v-if="option == product.title">
            <div class="prompt">Enter your pledge</div>
            <div class="pledge-input">
                <div>
                    <input type="number" :value="product.pledge" :min="product.pledge">
                </div>
                <button class="btn" @click="$emit('pledge', $event.target.previousSibling.firstChild,)">Continue</button>
            </div>
        </div>
    </div>
</template>

<script>
export default{
    name:'PledgeCard',
    data(){
        return{
            pledgeAmount:null,
        }
    },
    mounted(){
        console.log(this.option);
    },
    props:{
        products:{
            type: Array,
            required:true,
        },
        option:{
            type:String
        }
    },
    methods:{
        isChecked(radio){
            if(this.option == radio){
                return true
            } else{
                return false
            }
        }
    }
}
</script>

<style scoped>
.container{
    border:0.01rem solid var(--dark-gray);
    border-radius:0.6rem;
    margin-bottom:1.3rem;
    padding: 1.3rem 0;
}

input:invalid {
  border: solid red 3px;
  color:red;
}

.container > div{
    padding:0 1.3rem;
}
.container > div> div:first-of-type{
    display:flex;
    gap:15px;
    align-items: center;
}

h4{
    color:var(--black);
    font-size: 14px;
}

.pledge{
    color:var(--mod-cyan);
    font-weight: 500;
    margin-top:0.5rem;
}

.descr{
    padding:0.8rem 0;
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

.action{
    border-top:0.01rem solid var(--dark-gray);
}

.prompt{
    display: flex;
    justify-content: center;
    padding:1rem 0;
}

.pledge-input{
    display:flex;
    justify-content: space-between;
}

.pledge-input input{
    outline: none;
    border:1px solid var(--dark-gray);
    padding:0.8rem 1.6rem;
    border-radius: 1.4rem;
    max-width: 90px;
    color:var(--black);
    font-size: 1rem;
    cursor: pointer;
}

.pledge-input >div {
    position: relative;
}

.pledge-input >div::before{
    content:'$';
    font-size: 1rem;
    position: absolute;
    top:50%;
    left:15px;
    transform: translateY(-50%);
}

.action .btn{
    padding:0.8rem 1.6rem;
    border-radius: 1.4rem;
}

input[type=number]::-webkit-inner-spin-button, 
input[type=number]::-webkit-outer-spin-button { 
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    margin: 0; 
}

@media (min-width:1025px){
.container> div:first-of-type{
    display:flex;
    flex-wrap: wrap;
}

.remaining{
    order:1;
    padding-bottom: 0;
    margin-left:auto
}

.descr{
    width:100%;
    order:2;
    margin-left:30px;
}

label > div {
    display:flex;
    gap:15px;
}

.pledge{
    margin-top:0;
}

.action{
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding-top:1rem!important;
}

.prompt{
    display:block;
    padding: 0;
}
.pledge-input{
    gap:20px;
}
}
</style>