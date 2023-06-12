<template>
    <div class="my-block" ref="myBlock">
        <div ref="inone">01</div>
        <div ref="intwo">02</div>
        <div ref="inthree">03</div>
        <div ref="infour">04</div>   
    </div>
</template>

<style>
    .my-block{        
        /* --bl-height: calc(100vw - (2 * 5vw)); */
        --bl-height: 1000px;
        --bl-width: var(--bl-height);
        
        border-radius: var(--bl-height);
        /* border:dashed 10px #000000; */

        background-color: blueviolet;
        color: white;       
        position: absolute;

        height: var(--bl-height);
        width: var(--bl-width);
        top: calc(50% - (var(--bl-height) / 2));
        left: 5vw;
    }
    .my-block > div{
        --blin-height: 75px;
        --blin-width: var(--blin-height);
        --myvar: 0;

        border-radius: 50%;
        position: absolute;
        background-color: #ff0000;
        height: var(--blin-height);
        width: var(--blin-width);
        font-size: 2rem;
        justify-content: center;
        line-height: 1;
        display: flex;
        align-items: center;
        top: calc(50% - (var(--blin-height) / 2));
        left: calc(50% - (var(--blin-height) / 2));
       
        transform: rotate(calc(var(--myvar) * 1deg)) translate(calc(var(--bl-height) / 2)) rotate(calc(var(--myvar) * -1 * 1deg));
    }
   
</style>

<script >
    import { gsap } from "gsap";
    export default {
        mounted() {
            const block = this.$refs.myBlock;
            const blockChild = [
                this.$refs.inone,
                this.$refs.intwo,
                this.$refs.inthree,
                this.$refs.infour,
            ]

            console.log(blockChild)
            // return;
            blockChild.forEach((element, index) => { 
                gsap.to(element, 
                {
                    "--myvar": 360,
                    // rotation: "360",
                    // transform: "rotate(360deg) rotate(-360deg)",
                    duration: 3 + (0.1 * index), 
                    repeat: -1,
                    ease: "linear",

                    // rotation: 360,
                    // transformOrigin: '50% 50%',
                    // x: Math.cos((index / blockChild.length) * 2 * Math.PI) * 0,
                    // y: Math.sin((index / blockChild.length) * 2 * Math.PI) * 0,
                    // repeat: -1, 
                    // ease: 'power1.inOut',
                    // duration: 2,
                    delay: index * 0.2
                });
            })
            
        },
    };
</script>