<script>
    export let show = true;
</script>

{#if show}
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <div class="bg" on:click>
        <div class="modal">
            <slot></slot>
        </div>
    </div>
{/if}

<style>
    .bg {
        left: 0;
        top: 0;
        width: 100%;
        height: 100%;
        position: fixed;
        background: rgba(0, 0, 0, 0.8);
        z-index: 1;
    }

    .modal {
        padding: 20px;
        border-radius: 5px;
        width: 200px;
        text-align: center;
        margin: 10% auto;
        background: #fff;
        font-size: 20px;
        color: white;
        background-color: #444452;
    }
</style>

