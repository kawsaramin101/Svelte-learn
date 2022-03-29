<script>
    import { createEventDispatcher} from "svelte"
    
    let dispatch = createEventDispatcher();
    
    let name;
    let beltColour;
    let age;
    let skills = [];
    
    function handleSubmit() {
        const ninja = {
            name,
            beltColour: beltColor,
            age,
            skills,
            id: Math.random()
        };
        dispatch("addNinja", ninja);
    };
</script>

<form on:submit|preventDefault={handleSubmit}>
    <input type="text" bind:value={name} placeholder="Name" />
    <input type="number" bind:value={age} placeholder="Age" />
    <label>Belt Color:</label>
    <select bind:value={beltColor}>
        <option value="black">Black</option>
        <option value="orange">Orange</option>
        <option value="yellow">Yellow</option>
        <option value="green">Green</option>
    </select>
    <label>Skills:</label>
    <input type="checkbox" bind:group={skills} value="fighting"/>Fighting<br/>
    <input type="checkbox" bind:group={skills} value="sneaking"/>Sneaking<br/>
    <input type="checkbox" bind:group={skills} value="running"/>Running<br/>
    <br/>
    <button>Add Ninja</button>
</form>

<style>
    
</style>

