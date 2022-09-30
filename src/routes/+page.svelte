<style>
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
        width: 150px;
        height: 150px;
        border: 1px solid black;
    }
</style>

<script lang="ts">
    import Draggable from "./Draggable.svelte";
</script>

<div class="board-games-box">
    <div class="box">
        <span>1</span>
    </div>
    <div class="box">
        <span>2</span>
    </div>
    <div class="box">
        <span>3</span>
    </div>
    <div class="box">
        <span>4</span>
    </div>
    <div class="box">
        <span>5</span>
    </div>
    <div class="box">
        <span>6</span>
    </div>
    <div class="box">
        <span>7</span>
    </div>
    <div class="box">
        <span>8</span>
    </div>
    <div class="box">
        <span>9</span>
    </div>
</div>

<Draggable>
    <h1>
        Click me
    </h1>
</Draggable>
