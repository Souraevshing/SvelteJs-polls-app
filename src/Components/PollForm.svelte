<script>
    import { createEventDispatcher } from 'svelte'
    let fields = {question:'', ans1: '', ans2:''}
    let errors = {question:'', ans1: '', ans2:''}
    let valid = false
    let dispatch = createEventDispatcher()

    const handleSubmit = () => {
        valid = true
        //validating question
        if (fields.question.trim().length < 1) {
            valid = false
            errors.question = "Can't be left empty"
        } else {
            errors.question=''
        }

        //validating answer 1
        if (fields.ans1.trim().length < 1) {
            valid = false
            errors.ans1 = "Can't be left empty"
        } else {
            errors.ans1=''
        }

        //validating answer 2
        if (fields.ans2.trim().length < 1) {
            valid = false
            errors.ans2 = "Can't be left empty"
        } else {
            errors.ans2=''
        }

        if(valid){
            let poll = {...fields, votes1:0, votes2:0, id:Math.random()}
            dispatch('add',poll)
        }
    }
</script>

<form on:submit|preventDefault={handleSubmit}>
    <div class="form-field">
        <label for="question">Question : </label>
        <input type="text" id="question" bind:value={fields.question}>
        <span class="error">{errors.question}</span>
    </div>
    <div class="form-field">
        <label for="ans1">Answer 1 : </label>
        <input type="text" id="ans1" bind:value={fields.ans1}>
        <span class="error">{errors.ans1}</span>
    </div>
    <div class="form-field">
        <label for="ans2">Answer 2 : </label>
        <input type="text" id="ans2" bind:value={fields.ans2}>
        <span class="error">{errors.ans2}</span>
    </div>
    <button>Add Poll</button>
</form>

<style>
    form{
        width: 400px;
        margin: 0 auto;
        text-align: center;
    }

    .form-field{
        margin: 18px auto;
    }

    input{
        width: 100%;
        border-radius: 3px;
        background-color: rgb(234, 241, 239);
        color: rgb(26, 39, 34);
        outline-style: none;
    }

    label{
        margin: 10px auto;
        text-align: left;
    }

    .error{
        color: white;
        font-weight: bold;
        letter-spacing: 1.5px;
        background: red;
        font-size: 10px;
        border-radius: 8px;
        font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    }

    button{
        color: whitesmoke;
        background: green;
        padding-top: 5px;
        border-radius: 3px;
        cursor: pointer;
    }
</style>