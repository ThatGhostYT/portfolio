<script lang="ts">
    let blob: HTMLDivElement;

    function followMouse({ clientX, clientY }: HTMLElementEventMap["mousemove"]){
        blob.animate({
            left: `${clientX}px`,
            top: `${clientY}px`
        },{ duration: 3000, fill: "forwards" });
    }
</script>

<svelte:body on:mousemove={followMouse}/>
<div id="blob" bind:this={blob}></div>
<div id="blur"></div>

<style>
    @keyframes rotate{
        from{
            rotate: 0deg;
        }

        50%{
            scale: 1 1.5;
        }

        to{
            rotate: 360deg;
        }
    }

    #blob{
        height: 34vmax;
        aspect-ratio: 1;
        background: #0099ff;
        position: absolute;
        border-radius: 50%;
        left: 50%;
        top: 50%;
        translate: -50% -50%;
        animation: rotate 20s infinite;
    }

    #blur{
        height: 100%;
        width: 100%;
        z-index: 2;
        backdrop-filter: blur(12vmax);
    }
</style>