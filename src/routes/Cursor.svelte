<script>
    export let x;
    export let y;
    export let color;
    export let name;
</script>

{#if x && y}
    <div
        style={`position: absolute; left: 0; top: 0; transition: "transform 0.5s cubic-bezier(.17,.93,.38,1)"; transform: translateX(${x}px) translateY(${y}px)`}
    >
        <svg width="24" height="36" viewBox="0 0 24 36" fill="none" stroke={color} xmlns="http://www.w3.org/2000/svg">
            <path
                d="M5.65376 12.3673H5.46026L5.31717 12.4976L0.500002 16.8829L0.500002 1.19841L11.7841 12.3673H5.65376Z"
            />
        </svg>

        <div
            style={`backgroundColor: ${color}; borderRadius: 4; position: absolute; top: 20px; left: 10px; padding: 5px 10px`}
        >
            <p style="whiteSpace: nowrap; fontSize: 13; color: white;">
                {name}
            </p>
        </div>
    </div>
{/if}
