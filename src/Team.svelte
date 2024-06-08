<script>
    export let team;
    export let score;
    export let gameOver;
    let isBtnDisabled = false;

    const add = () => {
        score += 1
    }

    const minus = () => {
        if (score > 0) {
            score -= 1;

        } else {
            isBtnDisabled = true;
        }
    }

</script>

<div class="flex-col" style="border: 3px dashed {team.toLowerCase()}">
    <div class="item">
        <h3>{team} Team: {score}</h3>
        <div class="grid-2">
            <button disabled={gameOver} class="btn btn-plus" on:click={add}> &plus; </button>
            <button disabled={gameOver} class="btn btn-minus" on:click={minus} >  &minus; </button>        
        </div>
    </div>
</div>

<style>

    .item {
        padding: 20px;
        text-align: center;
    }

    .grid-2 {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        grid-gap: 5px;
        margin: 20px auto;
        max-width: 105px;
    }

    .btn {
        color: #fff;
        width: 50px;
        height: 50px;
        border: 1px solid #ededed;
        border-radius: 5px;
        font-size: 24px;
        text-align: center;
        padding: 5px;
    }

    .btn-plus {
        background: green;
    }

    .btn-minus {
        background: red;
    }

    h3 {
        color: #333;
        font-size: 22px;
    }
</style>