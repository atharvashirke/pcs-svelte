<script>
    import Typewriter from "svelte-typewriter";
    import { Canvas } from '@threlte/core'
    import Scene from "$lib/components/SplashScene.svelte"

    let index = 0

    let platitudes = [
        "A community dedicated to diverse thought.",
        "A community built for equity. ", 
        "A community of innovators.", 
        "A community for everyone."
    ]

    const rewrite = () => {
    }
</script>

<div class="content">
    <div class="animation">
        <Canvas>
            <Scene />
        </Canvas>
    </div>
    
    
    <Typewriter mode={'loopOnce'} interval={50}>
        {#each platitudes as platitude}
            <h1>{platitude}</h1>
        {/each}
    </Typewriter>
</div>


<style>
    .animation {
        position: absolute;
        width: 100%;
        height: 100%;
        overflow: hidden;
    }

    h1 {
        font-size: 3rem;
        font-weight: 700;
        text-align: center;
        margin: 0;
        padding: 0;
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
    }
</style>

