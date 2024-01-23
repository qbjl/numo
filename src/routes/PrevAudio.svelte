<script>
    export let style;
    export let name;
    export let file;
    import WaveSurfer from 'wavesurfer.js';
    import { onMount, afterUpdate } from 'svelte';
    let wavesurfer;
    let wvcontainer;
    onMount(() => {
        wavesurfer = WaveSurfer.create({
            container: wvcontainer,
            waveColor: '#999',
            progressColor: '#333',
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

<div class="prevc">
    <div class="preview" style={style}>
        <div class="waveform" bind:this={wvcontainer}></div>
    </div>
    <span>{name}</span><img src="/vol.png" alt="play" on:click={play_audio}/>
</div>