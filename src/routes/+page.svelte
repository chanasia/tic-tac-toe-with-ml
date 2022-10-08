<style lang="scss">
    *{
        padding: 0;
        margin: 0;
        box-sizing: border-box;
    }

    .board-games-box{
        display: inline-grid;
        grid-template-columns: repeat(3, 1fr);
    }

    .board-games-box .box{
        background-color: rgb(254, 199, 199);
        width: 100px;
        height: 100px;
        border: 1px solid black;
    }

    .container{
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        gap: 1rem;
    }

    .board-p1, .board-p2{
        display: flex;
        flex-direction: column;
        .small, .median, .large{
            width: 100px;
            height: 100px;
            border: 1px solid black;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
        }

        .small{
            font-size: 40px;
            font-weight: 800;
        }
            .median{
            font-size: 70px;
            font-weight: 800;
        }
            .large{
            font-size: 100px;
            font-weight: 800;
        }
    }
</style>

<script lang="ts">
	import type { checkers } from "../interfaces/iDraggable";
	import Draggable from "./Draggable.svelte";


    const checkersX: checkers[] = [
        {checkerSize: 'small', checkerType: 1, src: 'x'},
        {checkerSize: 'median', checkerType: 1, src: 'x'},
        {checkerSize: 'large', checkerType: 1, src: 'x'}
    ]
    const checkersO: checkers[] = [
        {checkerSize: 'small', checkerType: -1, src: 'o'},
        {checkerSize: 'median', checkerType: -1, src: 'o'},
        {checkerSize: 'large', checkerType: -1, src: 'o'}
    ]

    const boardBoxs = [

    ]

    function dragCheckers(ev: DragEvent, item: checkers){
        ev.dataTransfer?.setData("checkerSize", item.checkerSize)
        ev.dataTransfer?.setData("checkerType", item.checkerType.toString())
        ev.dataTransfer?.setData("src", item.src)
    }

    function dragOverCheckers(e: DragEvent){
        e.preventDefault()
    }

    function dropCheckers(e: DragEvent){
        e.preventDefault()
        const src = e.dataTransfer?.getData("src")
    }
</script>


<div class="container">
    <div class="board-p1">
        {#each checkersX as item}
        <div class={item.checkerSize} draggable={true} on:dragstart={ev => dragCheckers(ev, item)}>
            <span>{item.src}</span>
        </div>
        {/each}
    </div>
    <div class="board-games-box">
        {#each Array(9) as _, i}
            <div class="box" on:dragover={dragOverCheckers} on:drop={dropCheckers}>
                <!-- <span>{i+1}</span> -->
            </div>
        {/each}
    </div>
    <div class="board-p2">
        {#each checkersO as item}
        <div class={item.checkerSize} draggable={true} on:dragstart={ev => dragCheckers(ev, item)}>
            <span>{item.src}</span>
        </div>
        {/each}
    </div>
</div>



