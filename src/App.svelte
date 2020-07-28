<script>
	import VersionList from "./routes/VersionList.svelte";
	import Feedback from "./routes/Feedback.svelte";
	import Welcome from "./routes/Welcome.svelte";
	
    let showVersion = false;
    const toggleVersion = () => {
		showVersion = !showVersion;
		showFeedback = false;
	}

	let showFeedback = false;
    const toggleFeedback = () => {
		showFeedback = !showFeedback;
		showVersion = false;
    }
</script>

<div class="hero-image">
	<div class="hero-text">
		<span class="title">My First Unity Game</span>
	</div>
</div>

<div class="mobile-title">
	My First Unity Game
</div>

<table class="toggle">
	<tr>
		<td>
		    <button on:click={toggleVersion}>Show Versions</button>
		</td>
		<td>
			<button on:click={toggleFeedback}>Show Feedback</button>
		</td>
	</tr>
</table>    

{#if showVersion}
	<VersionList/>
{/if}

{#if showFeedback}
	<Feedback/>
{/if}

{#if !showVersion && !showFeedback}
	<Welcome/>
{/if}

<style>
    .toggle {
        margin: auto;
        width: 1000px;
        margin-top: 1rem;
        margin-bottom: 5rem;
	}
	
	tr {
		width: 1000px;
		height: 70px;
	}
	
	td {
		width: 500px;
		height: 70px;
	}

    .toggle tr td button {
        text-align: center;
        margin: auto;
        width: 100%;
        height: 100%;
        background-color: rgb(175, 76, 76);
        border: none;
        color: white;
        padding: 15px 32px;
        text-decoration: none;
        display: inline-block;
		font-size: 35px;
		cursor: pointer;
    }

	.hero-image {
		background-image: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), url('/img/hero-image.png');
		height: 60%;
		background-position: center;
		background-repeat: no-repeat;
		background-size: cover;
		position: relative;
		margin-bottom: 3rem;
	}

	.hero-text {
		text-align: center;
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		color: white;
	}

	.hero-text .title {
		font-size: 110px;
	}

	.hero-text span {
		font-size: 40px;
		text-shadow: 0px 0px 8px rgba(0, 0, 0, 0.85);
		color: lightgray;
	}

	.mobile-title {
		display: hidden;
		font-size: 0;
		margin: 0;
		padding: 0;
	}

	@media all and (max-width: 800px) {
		.hero-image {
			background-image: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), url('/img/hero-image.png');
			height: 60%;
			background-position: center;
			background-repeat: no-repeat;
			background-size: cover;
			position: relative;
			margin-bottom: 3rem;
		}

		.hero-text {
			text-align: center;
			position: absolute;
			top: 50%;
			left: 50%;
			transform: translate(-50%, -50%);
			color: white;
		}

		.hero-text .title {
			font-size: 70px;
		}

		.hero-text span {
			font-size: 20px;
			text-shadow: 0px 0px 8px rgba(0, 0, 0, 0.85);
		}
	}

	@media all and (max-width: 400px) {
		.hero-image {
			display: none;
		}

		.mobile-title {
			display: visible;
			color: #36353f;
			text-align: center;
			font-size: 50px;
		}
	}
</style>