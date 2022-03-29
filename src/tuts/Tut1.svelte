<script>
    import Modal from "../components/Modal.svelte";
    import AddNinjaForm from "../components/addNinjaForm.svelte";
    
    let showModal = false;
    
    function toggleModal() {
        showModal = !showModal
    }
    
    let ninjas = [
        { name: 'luigi', beltColour: 'brown', age: 35, id: 1 },
        { name: 'yoshi', beltColour: 'black', age: 25, id: 2 },
        { name: 'mario', beltColour: 'orange', age: 45, id: 3 },
        { name: 'luigi', beltColour: 'brown', age: 35, id: 4 },
        { name: 'yoshi', beltColour: 'black', age: 25, id: 5 },
        { name: 'mario', beltColour: 'orange', age: 45, id: 6 },
        { name: 'luigi', beltColour: 'brown', age: 35, id: 7 },
        { name: 'yoshi', beltColour: 'black', age: 25, id: 8 },
    ];
    
    function handleDelete(id) {
        ninjas = ninjas.filter(ninja => ninja.id !== id);
    };
    
    function addNinja(event) {
        console.log(event.detail);
        ninjas = [event.detail, ...ninjas];
        showModal = false;
    };
    
</script>

<Modal {showModal} message="Hey I am from props" isPromo=true on:click={toggleModal}>
    <AddNinjaForm on:addNinja={addNinja}/>
    <div slot="title">
        <h3>I am h3, I am a h3</h3>
    </div>
</Modal>
<button on:click={toggleModal}>Open Modal</button>
<div>
    {#if ninjas.length > 5 }
    <b>Wow, So many Ninjas!</b>
    {:else if ninjas.length == 5}
    <b>Only 5 Ninjas</b>
    {:else if ninjas.length === 0}
    <span></span>
    {:else}
    <b>So less Ninja</b>
    {/if}
    {#each ninjas as ninja (ninja.id)}
    <div>
        <h4>{ninja.name} is {ninja.age} years old and has a 
            <span style="color: {ninja.beltColour}">{ninja.beltColour}</span> belt 
        </h4>
        {#if ninja.beltColour === "black" }
            <b>MASTER 😎</b>
            <br/>
        {/if}
        <button on:click={() => {handleDelete(ninja.id) } }>Delete</button>
        <hr/>
    </div>
    {:else }
    <b>No Ninjas! Wow nobody wanna become Ninja this days 😒</b>
    {/each}
    
</div>