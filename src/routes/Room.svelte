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
            users = Array.from(awareness.getStates().values()).map((element) => {
                return {
                    name: element.name,
                    color: element.color,
                    x: element?.cursor?.x,
                    y: element?.cursor?.y
                };
            });
        });
    });
</script>

{#each users as user}
    <Cursor name={user.name} color={user.color} x={user.x} y={user.y} />
{/each}
