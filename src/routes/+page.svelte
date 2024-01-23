<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>numo</title>
    <link rel="stylesheet" href="style.css">
</head>

<script>
    import Audio from './Audio.svelte';
    import { onMount } from 'svelte';
    import Sidebar from './Sidebar.svelte';

    let audios = [
        { style: "width: 150px", name: "kick", file: "BN_kick_houseless.wav", x: 0, y: 0 },
        { style: "width: 75px", name: "snare", file: "BN_snare_whomp.wav", x: 100, y: 50 }
    ];

    function handleClone(e) {
        if (!e.detail) return;
        const { name, file, x, y } = e.detail;
        audios = [...audios, { name, file, x, y }];
    }
</script>

<div class="layout">
    <div class="sidebar"> 
        <Sidebar />
    </div>
    <div class="main" id="main">
        {#each audios as audio, index (index)}
            <Audio style={audio.style} name={audio.name} file={audio.file} on:clone={handleClone} x={audio.x} y={audio.y} />
        {/each}
    </div>
</div>