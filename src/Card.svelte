<script>
    import Parse from 'parse/dist/parse.min.js';

	export let name = '';
	export let quantity = 0;
    export let price = 0;
    export let handleClick;

</script>

<div class="card">
	 <h3>{name}</h3>
	 <div class="details">
        <p>Price: ${price}</p>
        <p>Quantity: {quantity == 0 ? "out of stock" : quantity}</p>
     </div>
     <div>
        <button on:click={handleClick}>Delete</button>
     </div>
</div>

<style>
    .card{
        display: flex;
        flex-direction: column;
        gap: 1.9rem;
        padding: 1rem;
        border-radius: 12px;
        background-color: #e2e2e2;
        color: #1F2124;;
        inline-size: 100%;
    }

    .details{
        display: flex;
        gap: 3rem;
    }

    .details p{
        font-size: 14px;
        font-weight: 500;
        color: #888888;
    }
</style>