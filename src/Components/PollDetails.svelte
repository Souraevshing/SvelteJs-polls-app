<script>
    export let poll=[]
    import { createEventDispatcher } from "svelte";
    //reactive values
    $:totalVotes = poll.votes1+poll.votes2
    $:percent1 = Math.floor(100/totalVotes * poll.votes1)
    $:percent2 = Math.floor(100/totalVotes * poll.votes2)

    const dispatch = createEventDispatcher()

    const handleVote = (option,id) => {
        dispatch('vote', {option:option, id:id})
    }
</script>

<div class="poll">
    <h3>{poll.question}</h3>
    <p>Total votes : {totalVotes}</p>
    <div class="answer" on:click={()=>handleVote('1',poll.id)}>
        <div class="percent percent-1" style="width:  {percent1}%">
            <span>{poll.ans1} ({poll.votes1})</span>
        </div>
    </div>
    <div class="answer" on:click={()=>handleVote('2',poll.id)}>
        <div class="percent percent-2" style="width: {percent2}%">
            <span>{poll.ans2} ({poll.votes2})</span>
        </div>
    </div>
</div>

<style>
    h3{
        margin: 0 auto;
        color: gray;
    }

    p{
        margin-top: 6px;
        font-size: 14px;
        color: rgb(51, 172, 27);
    }

    .answer{
        background: white;
        cursor: pointer;
        margin: 10px auto;
        position: relative;
    }

    .answer:hover{
        opacity: 0.6;
    }

    span{
        display: inline-block;
        padding: 10px 20px;
    }
</style>