<script>
    import { onMount, getContext } from "svelte";
    import Cursor from "./Cursor.svelte";

    const awareness = getContext("awareness");

    let users = [];

    onMount(() => {
        window.addEventListener("pointermove", (e) => {
            awareness.setLocalStateField("cursor", {
                x: e.clientX,
                y: e.clientY
            });
        });
        awareness.on("change", () => {
            users = awareness.getStates().entries();
        });
    });
</script>

{#each users as [clientID, user]}
    {#if clientID != awareness?.clientID}
        <Cursor name={user.name} color={user.color} x={user?.cursor?.x} y={user?.cursor?.y} />
    {/if}
{/each}
