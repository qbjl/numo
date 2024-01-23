<script>
    import { draggable } from '@neodrag/svelte';
    import { createEventDispatcher } from 'svelte';
    import { browser } from '$app/environment';
    export let style;
    export let name;
    export let file;
    export let x;
    export let y;
    import WaveSurfer from 'wavesurfer.js';
    import { onMount, afterUpdate } from 'svelte';
    let wavesurfer;
    let wvcontainer;
    const dispatch = createEventDispatcher();
    onMount(() => {
        wavesurfer = WaveSurfer.create({
            container: wvcontainer,
            waveColor: '#000000bc',
            progressColor: '#000000dd',
            cursorColor: 'transparent',
            barWidth: 1,
            barHeight: 1,
            barGap: 1,
            height: 45,
            autoCenter: true,
            interact: false,
            url: file
        });
    })

    afterUpdate(() => {
        if (wavesurfer) {
            wavesurfer.load(file);
        }
    })

    function play_audio() {
        if (!wavesurfer) return;
        wavesurfer.play();
    }

    function clone() {
        dispatch('clone', { name, file, x, y: y - 70 });
    }
</script>

<div class="audio" use:draggable={{ handle: '.top', bounds: 'parent', grid: [25, 70], defaultPosition: { x, y } }} style={style}>
    <div class="top">{name}<img src="/vol.png" alt="play" on:click={play_audio}/><img src="/clone.png" alt="clone" on:click={clone}/></div>
    <div class="waveform" bind:this={wvcontainer}></div>
</div>