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

<Canvas>
    <Scene />
</Canvas>

<Typewriter mode={'loopOnce'} interval={50}>
    {#each platitudes as platitude}
        <h1>{platitude}</h1>
    {/each}
</Typewriter>

