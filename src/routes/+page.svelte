<script>
    import { setContext } from "svelte";
    import { browser } from "$app/environment";
    import * as Y from "yjs";
    import { WebrtcProvider } from "y-webrtc";
    import Room from "./Room.svelte";

    const USER_COLORS = [
        "#1a1c2c",
        "#E57373",
        "#9575CD",
        "#4FC3F7",
        "#81C784",
        "#144cb5",
        "#FF8A65",
        "#F06292",
        "#7986CB"
    ];

    const USER_NAMES = ["Daniel", "John", "Mary", "Harry", "Nico", "Ricky", "Sam", "Tom"];

    const random = (arr) => {
        return arr[Math.floor(Math.random() * arr.length)];
    };

    const name = random(USER_NAMES);
    const color = random(USER_COLORS);

    let awareness;
    if (browser) {
        const ydoc = new Y.Doc();
        const provider = new WebrtcProvider("foobar", ydoc, {
            signaling: ["ws://localhost:4444"]
        });

        awareness = provider.awareness;
        setContext("awareness", awareness);
        awareness.setLocalState({ name: name, color: color });

        console.log(awareness.getStates());
    }
</script>

Hello world

<p>Current name: {name}</p>

<Room />
