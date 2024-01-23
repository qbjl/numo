<script>
    let dropdownVisible = false;
    export let style;
    export let text;
    export let href;

    text = text.split(', ');
    href = href.split(', ');
</script>

<div class="dd-contain" role="button" 
    on:mouseover={() => dropdownVisible = true} 
    on:mouseout={() => dropdownVisible = false}
    on:focus={() => dropdownVisible = true} 
    on:blur={() => dropdownVisible = false}
    tabindex="0">
    <slot/>
    <span class="dd-menu" class:visible={dropdownVisible} style={style}>
        {#each href as link, id}
            <span><a href={link}>{@html text[id]}</a></span>
        {/each}
    </span>
</div>