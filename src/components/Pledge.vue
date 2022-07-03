<template>
    <div class="container">
        <div>
            <div>
                <input type="radio" id="no-reward" @change="checked = !checked">
                <label for="no-reward">
                    <div>
                        <h4>Bamboo Stand</h4>
                        <div class="pledge">Pleadge with $25 or more</div>
                    </div>
                </label>
            </div>
            <div class="descr">
                You get an ergonomic stand made of natural bamboo. You've helped us launch our promotional campaign, and you’ll be added to a special Backer member list.
            </div>
            <div class="remaining"><span>101</span> left</div>
        </div>
        <div class="action" v-if="checked">
            <div class="prompt">Enter your pledge</div>
            <div class="pledge-input">
                <div>
                    <input type="number">
                </div>
                <button class="btn">Continue</button>
            </div>
        </div>
    </div>
</template>

<script>
export default{
    name:'PledgeCard',
    data(){
        return{
            checked:false,
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
    border-top:0.01rem solid var(--dark-gray)
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