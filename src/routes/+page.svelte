<script>
    import Typewriter from "svelte-typewriter";
    import { Canvas } from '@threlte/core'
    import { onMount } from 'svelte'
    import Scene from "$lib/components/SplashScene.svelte"
    import { Button, Heading, P, A } from 'flowbite-svelte';

    let platitudes = [
        "A community dedicated to diverse thought.",
        "A community built for equity. ", 
        "A community of innovators.", 
        "A community for everyone."
    ]
</script>

<div class="block">
    <div class="animation -z-50">
        <Canvas>
            <Scene />
        </Canvas>
    </div>
    <div class="typewriter">
        <Typewriter mode={'loopOnce'} interval={50}>
            {#each platitudes as platitude}
                <h1 class="text-black pointer-events-none select-none text-lg">{platitude}</h1>
            {/each}
        </Typewriter>
    </div> 
</div>






<style>
    .animation {
        position: absolute;
        width: 100%;
        height: 100%;
        overflow: hidden;
    }

    .typewriter {
        margin: 0;
        padding: 0;
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
    }

    h1 {
        font-size: 3rem;
        font-weight: 700;
        text-align: center;
    }
</style>

