<script>
    let theme;
	$: switchTheme = theme === "🌙" ? "💡" : "🌙";
	export let isDark;
	if (isDark) {
		theme = "🌙"
		window.document.body.classList.toggle('dark-mode')
	}
    function toggle() {
        theme = switchTheme
	    window.document.body.classList.toggle('dark-mode')
    }
</script>

<button on:click={toggle}>
	{switchTheme}
</button>

<style>
    button {
		/* background: var(--bg-color); */
		/* border: 1.5x solid var(--text-color); */
		border: 0px solid var(--text-color);
		/* border-radius: 10px; */
		color: var(--text-color);
		padding: 8px 8px;
        transition: background-color 0.3s
	}
	
	button:active {
		background: inherit;
	}
</style>