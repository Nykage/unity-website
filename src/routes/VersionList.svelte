<script>
    import {versionlist} from './data-versionlist.js'
    import {onMount} from 'svelte'

    onMount( async() => {
        const url = 'https://myunitygame.truudeli15.net/back/get-versions.php'
        let res = await fetch(url)
        res = await res.json()
        let data = await res.data
        $versionlist = res.data
        console.log(res.data)
    })

    let showText = false;
    const toggleText = () => {
        showText = !showText;
    }
</script>

<div class="toggle">
    <button on:click={toggleText}>Show Details</button>
</div>

<div class="flex-container">
    {#each $versionlist as version (version.VersionID)}
        <div class="container">
            <img src="{version.ExampleSprite}" alt="sprite">
            <span>{version.VersionNumber}</span>
            {#if showText}
            <div class="text">
                <a href="{version.DownloadLink}" target="_blank"><b>Download this version here</b></a>
                <br>
                <span>{version.Hint}</span>
            </div>
            {/if}
        </div>
    {/each}
</div>

<style>
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
        justify-content: center;
        flex-direction: column-reverse;
        margin-bottom: 5rem;
    }

    .container {
        font-size: 70px;
        color: #43b638;
        padding: 1rem;
        box-sizing: border-box;
        align-items: center;
        flex: auto;
        max-width: 500px;
        text-align: center;
        margin-bottom: 2rem;
    }

    .container:hover {
        background-color: rgb(206, 204, 204);
    }

    .container img {
        width: 45px;
        height: auto;
        text-align: center;
    }

    .container span {
        text-align: center;
    }

    .text {
        margin-top: 1rem;
        padding: 10px;
        font-size: 25px;
    }

    .text span {
        text-align: center;
    }

    .text a {
        font-size: 35px;
        text-decoration: none;
    }

	@media all and (max-width: 400px) {
        .flex-container {
            flex-direction: column;
        }

        .container span {
            text-align: center;
        }

        .container img {
            text-align: center;
        }
    }
</style>