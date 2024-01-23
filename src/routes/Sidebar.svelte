<script>
    import Dropdown from './Dropdown.svelte';
    import PrevAudio from './PrevAudio.svelte';
    let dropdownVisible = [false, false, false, false];
</script>

<div class="topbar">
    <span class="title">numo</span>
    <button class="right side">new</button>
    <Dropdown style="" text='project, instrument, pattern' href='#, #, #'>
        <button class="left side">...</button>
    </Dropdown>
    <div class="dd-contain" role="button" 
        on:mouseover={() => dropdownVisible[1] = true} 
        on:mouseout={() => dropdownVisible[1] = false}
        on:focus={() => dropdownVisible[1] = true} 
        on:blur={() => dropdownVisible[1] = false}
        tabindex="0">
        <button>file</button>
        <span class="dd-menu" class:visible={dropdownVisible[1]}>
            <span><a href="#">open <small>(ctrl+shift+o)</small></a></span>
            <span><a href="#">save <small>(ctrl+s)</small></a></span>
            <span><a href="#">export</a></span>
            <span><Dropdown style="left: 5rem" text='instrument, pattern, sample' href='#, #, #'><a href="#">import...</a></Dropdown></span>
            <span><Dropdown style="left: 5rem" text='import, reload, toggle' href='#, #, #'><a href="#">scripts...</a></Dropdown></span>
        </span>
    </div>
    <div class="dd-contain" role="button" 
        on:mouseover={() => dropdownVisible[0] = true} 
        on:mouseout={() => dropdownVisible[0] = false}
        on:focus={() => dropdownVisible[0] = true} 
        on:blur={() => dropdownVisible[0] = false}
        tabindex="0">
        <button>edit</button>
        <span class="dd-menu" class:visible={dropdownVisible[0]}>
            <span><a href="#">copy <small>(ctrl+c)</small></a></span>
            <span><a href="#">paste <small>(ctrl+v)</small></a></span>
            <span><a href="#">undo <small>(ctrl+z)</small></a></span>
            <span><a href="#">redo <small>(ctrl+y)</small></a></span>
            <span><a href="#">rename <small>(ctrl+r)</small></a></span>
            <span><Dropdown style="left: 5rem" text='volume, pitch' href='#, #'><span><a href="#">adjustments...</a></span></Dropdown></span>
            <span><Dropdown style="left: 5rem" text='fx <small>(ctrl+o)</small>, mixer, automation' href='#, #, #'><span><a href="#">quick open...</a></span></Dropdown></span>
        </span>
    </div>
</div><br>
<h3>loaded samples</h3><br>
<div class="audiolist">
    <PrevAudio name="kick" file="BN_kick_houseless.wav" />
    <PrevAudio name="snare" file="BN_snare_whomp.wav" />
</div>