<script lang="ts">
    export let left: Number = 30
    export let top: Number = 30
    let moving:boolean = false

    function start(){
        moving = true
    }

    function stop(){
        moving = false
    }

    function move(e:any){
        if(moving){
            left += e.movementX
            top += e.movementY
        }
    }
</script>

<style>
    .draggable{
        user-select: none;
        position:absolute;
        border: solid 1px gray;
        cursor: grab;
    }
</style>

<svelte:window on:mouseup={stop} on:mousemove={move}/>

<section on:mousedown={start} style="left: {left}px; top: {top}px;" class="draggable">
    <slot></slot>
</section>