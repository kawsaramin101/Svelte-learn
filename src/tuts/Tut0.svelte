<script>
    let firstName = "Yakamo";
    let lastName = "Torito";
    let beltColor = "Orange";

    $: fullname = `${firstName} ${lastName}`;
    $: {
        console.log(fullname);
        console.log("Hello")
        console.log(beltColor)
    }


    let count = 0;
    let error = "";

    function increase() {
        error = "";
        count += 1;
    };

    function decrease() {
        if (count == 0) {
            error = "Count cannot be less than 0";
            return;
        }
        count -= 1;
    };

</script>

<div>
    <h2>{fullname} has <span style="color : {beltColor}">{beltColor}</span> belt</h2>

    <input type="text" bind:value={firstName} placeholder="First Name" />
    <input type="text" bind:value={lastName} placeholder="Last Name" />
    <input type="text" bind:value={beltColor} placeholder="Belt name" />

    <br />
    <br />
    <p>
        count : {count}
    </p>
    <button on:click={increase}>+</button>
    <button on:click={decrease}>-</button>
    <p>
        {error}
    </p>
</div>