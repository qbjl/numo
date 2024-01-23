<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>numo</title>
    <link rel="stylesheet" href="style.css">
</head>

<script>
    import { draggable } from '@neodrag/svelte';
    import Audio from './Audio.svelte';
    import { onMount } from 'svelte';
    import Dropdown from './Dropdown.svelte';
    import Sidebar from './Sidebar.svelte';
    let dropdownVisible = [false, false, false, false];
</script>

<div class="layout">
    <div class="sidebar"> 
        <Sidebar />
    </div>
    <div class="main">
        <Audio style="width: 150px" name="kick" file="BN_kick_houseless.wav" x=0 y=0 />
        <Audio style="width: 75px" name="snare" file="BN_snare_whomp.wav" x=100 y=50 />
    </div>
</div>