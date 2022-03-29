<script>
    export let showModal = false;
    export let message = "I don't have any message, maybe the coder messed up";
    export let isPromo = false;
</script>

{#if showModal }
<div class="backdrop" class:promo={isPromo} on:click|self>
    <div class="modal">
        <button on:click>Close Modal</button>
        <p>{message}</p>
        <slot name="title"></slot>
        <slot></slot>
    </div>
</div>
{/if }

<style>
    .backdrop{
    width: 100%;
    height: 100%;
    position: fixed;
    background: rgba(0,0,0,0.8);
  }
  .modal{
    padding: 1em;
    border-radius: 10px;
    max-width: 400px;
    margin: 10% auto;;
    text-align: center;
    background: white;
  }
  .promo .modal{
    background: crimson;
    color: white;
  }
  
</style>