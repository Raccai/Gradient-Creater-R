<script>
    import Popup from "./Popup.svelte";

    let show = false;
    let styles = {
		color1: "#3a7dbb",
    	color2: "#19519a",
        direction: "180deg"
	}

	$: cssVarStyles = Object.entries(styles)
		.map(([key, value]) => `--${key}:${value}`)
		.join(';');

	$: backgroundImage = `background-image: linear-gradient(${styles.direction}, ${styles.color1}, ${styles.color2});`;

    const copy = () => {
		let copyText = document.getElementById("bgiText");
		copyText.select();
		navigator.clipboard.writeText(copyText.value);
		togglePopup();
    }

    const togglePopup = () => {
		show = !show;
	}
</script>

<Popup {show} on:click = {togglePopup} >Copied!</Popup>
<div class="main-body">
    <div class="display" style={cssVarStyles}></div>
    <div class="color-inputs">
        <input type="text" bind:value = {styles.direction} class="direction">
        <input type="color" bind:value = {styles.color1} class="color1">
        <input type="color" bind:value = {styles.color2} class="color2">
    </div>
    <div class="bottom-body">
        <textarea type="text" bind:value = {backgroundImage} class="bgiText" id="bgiText"></textarea>
        <button class="copy" on:click = {copy}>Copy</button>
    </div>    
</div>

<style>
    div.display {
        width: 300px;
        height: 300px;
        border-radius: 10px;
        margin: 40px auto;
        background-image: linear-gradient(var(--direction), var(--color1), var(--color2));
    }

    .color-inputs {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin: -30px 0 0 0;
    }

    .bottom-body {
        position: relative;
        display: flex;
        gap: 10px;
    }

    button.copy {
        width: 80px;
        border-radius: 10px;
        border: none;
        font-size: 15px;
        background-color: #6399D5;
        color: white;
        transition: all 0.2s ease;
        cursor: pointer;
    }

    button.copy:hover,
    button.copy:focus {
        border: 2px solid #6399D5;
        background-color: transparent;
        color: #6399D5;
    }   

    .bgiText {
        border: none;
        width: 220px;
        height: 80px;
        resize: none;
        background-color: #444452;
        border-radius: 10px;
        color: white;
    }

    .direction {
        padding: 30px auto;
        border: none;
        height: 35px;
        background-color: #444452;
        border-radius: 10px;
        color: white;
    }

    .direction:focus,
    .bgiText:focus {
        outline: none;
        border-bottom: 4px solid #6990BF;
    }

    .color1,
    .color2 {
        -webkit-appearance: none;
        -moz-appearance: none;
        appearance: none;
        width: 55px;
        height: 60px;
        background-color: transparent;
        border: none;
        cursor: pointer;
    }

    .color1::-webkit-color-swatch,
    .color2::-webkit-color-swatch {
        border-radius: 50px;
        border: none;
    }

    .color1::-moz-color-swatch,
    .color2::-moz-color-swatch {
        border-radius: 50px;
        border: none;
    }

    .color1:focus,
    .color2:focus {
        outline: 2px solid #6990BF; 
        border: none;       
    }
</style>