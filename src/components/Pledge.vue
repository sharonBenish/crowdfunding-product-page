<template>
    <div class="container">
        <div>
            <div>
                <input type="radio" id="no-reward">
                <label for id="no-reward">
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
        <div class="action">
            <div class="prompt">Enter your pledge</div>
            <div class="pledge-input">
                <input type="number">
                <button class="btn">Continue</button>
            </div>
        </div>
    </div>
</template>

<script>
export default{
    name:'Pledge',
}
</script>

<style scoped>
.container{
    border:0.01rem solid var(--dark-gray);
    border-radius:0.6rem;
    padding:1.3rem;
    margin-bottom:1.3rem;
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
    border: 1px solid red;
}

.prompt{
    border: 1px solid blue;
    display: flex;
    justify-content: center;
}

.pledge-input{
    display:flex;
    justify-content: space-between;
}

.pledge-input input{
    outline: none;
    border:1px solid var(--dark-gray);
    padding:1rem 1.6rem;
    border-radius: 1.5rem;
    max-width: 100px;
    position: relative;
}

.pledge-input input::before{
    content:'hi';
    width:10px;
    height:10px;
    border:1px solid blue;
    color:black;
    position: absolute;
    top:0;
    left:15px;
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
}
</style>