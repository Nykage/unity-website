<script>
    import {feedback} from './data-feedback.js'
    import {onMount} from 'svelte'

    onMount( async() => {
        const url = 'https://myunitygame.truudeli15.net/back/get-feedback.php'
        let res = await fetch(url)
        res = await res.json()
        let data = await res.data
        $feedback = res.data
        console.log(res.data)
    })

    let writeText = false;
        const toggleText = () => {
        writeText = !writeText;
    }
</script>

{#if !writeText}
<div class="toggle">
    <button on:click={toggleText}>Write Feedback</button>
</div>
{/if}
{#if writeText}
<div class="toggle">
    <button on:click={toggleText}>Return</button>
</div>
{/if}

{#if !writeText}
<div class="flex-container">
    {#each $feedback as comment (comment.FeedbackID)}
        <div class="container">
        <span class="author"><b>{comment.FeedbackAuthor} says:</b></span>
        <br>
        <span>{comment.FeedbackText}</span>
        </div>
    {/each}
</div>
{/if}

{#if writeText}
<div class="form-container">
    <form action="https://myunitygame.truudeli15.net/back/write-feedback.php" method="post">
        <span class="title">Short Feedback:</span> <br><input type="text" name="FeedbackText"><br>
        <span class="title">Your Name:</span> <br><input type="text" name="FeedbackAuthor"><br>
        <input type="submit" value="Submit">
    </form>
</div>
{/if}

<style>
    .form-container {
        max-width: 750px;
        display: flex;
        margin: 0 auto;
        justify-content: flex-start;
        align-items: center;
        margin-bottom: 5rem;
    }

    .title {
        text-align: center;
        color: #27b472;
        font-size: 35px;
        margin-bottom: 4rem;
        text-align: center;
    }
        
    input[type=text] {
        width: 750px;
        padding: 12px 20px;
        margin: 8px 0;
        box-sizing: border-box;
    }

    input[type=submit] {
        width: 750px;
        padding: 12px 20px;
        margin: 8px 0;
        box-sizing: border-box;
        background-color: #4CAF50;
        color: white;
        font-size: 25px;
    }

    input[type=submit]:hover {
        cursor: pointer;
    }

    @media all and (max-width: 400px) {
        .form-container {
            max-width: 250px;
            display: flex;
            margin: 0 auto;
            justify-content: flex-start;
            align-items: center;
            margin-top: 7rem;
        }
        
        .title {
            text-align: center;
            color: #27b472;
            font-size: 35px;
            margin-bottom: 4rem;
            text-align: center;
        }
        
        input[type=text] {
            width: 250px;
            padding: 12px 20px;
            margin: 8px 0;
            box-sizing: border-box;
        }
                    
        input[type=submit] {
            width: 250px;
            padding: 12px 20px;
            margin: 8px 0;
            box-sizing: border-box;
            background-color: #4CAF50;
            color: white;
            font-size: 25px;
        }    
    }

    .toggle {
        margin: auto;
        width: 375px;
        margin-top: 1rem;
        margin-bottom: 3rem;
    }

    .toggle button {
        text-align: center;
        margin: auto;
        width: 375px;
        height: 80px;
        background-color: #4CAF50; /* Green */
        border: none;
        color: white;
        padding: 15px 32px;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        font-size: 45px;
        cursor: pointer;
    }

    .flex-container {
        display: flex;
        margin: 0 auto;
        flex-flow: wrap;
        align-items: center;
        max-width: 1000px;
        justify-content: space-around;
        flex-direction: column-reverse;
        margin-bottom: 5rem;
    }

    .container {
        font-size: 30px;
        color: #43b638;
        padding: 1rem;
        box-sizing: border-box;
        align-items: center;
        flex: auto;
        max-width: 750px;
        cursor: pointer;
        text-align: center;
        margin-bottom: 3rem;
    }

    .container:hover {
        background-color: rgb(206, 204, 204);
    }

    .container span {
        text-align: center;
    }

    .container .author {
        text-align: center;
        font-size: 45px;
        color: #27b472;
    }

	@media all and (max-width: 400px) {
        .flex-container {
            flex-direction: column;
        }

        .container span {
            text-align: center;
        }
    }
</style>
