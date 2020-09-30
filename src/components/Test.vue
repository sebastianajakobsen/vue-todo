<template>
    <p>MouseXPosition: {{mouseX}} <br/> MouseYPosition: {{mouseY}}</p>
</template>

<script>

    import {useMousePosition} from "../functions/useMousePosition";

    export default {
        name: 'Test',

        components: {},
        setup() {
            const {x:mouseX, y:mouseY} = useMousePosition()

            return {
                mouseX,
                mouseY
            }
        }



    }
</script>
