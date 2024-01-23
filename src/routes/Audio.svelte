<script>
    import { draggable } from '@neodrag/svelte';
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
</script>

<div class="audio" use:draggable={{ handle: '.top', bounds: 'parent', grid: [25, 70], defaultPosition: { x, y } }} style={style}>
    <div class="top">{name}<img src="/vol.png" alt="play" on:click={play_audio}/></div>
    <div class="waveform" bind:this={wvcontainer}></div>
</div>