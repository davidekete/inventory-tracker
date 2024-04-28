<script>
    import Parse from 'parse/dist/parse.min.js';
    import { navigate } from "svelte-routing";

    let product = {
        name: "",
        quantity: "",
        price: "",
    }

    let addData = (event) => {
        event.preventDefault();
        try {
            const Inventory = new Parse.Object("Inventory");
            Inventory.set("name", product.name);
            Inventory.set("quantity", +product.quantity);
            Inventory.set("price", +product.price);
            Inventory.save().then(() => {
            console.log("New Product added successfully");
            navigate("/", { replace: true });
            });
        } catch (error) {
            console.log(error);
        }

    }

</script>

<form on:submit={addData}>
    <input type="text" placeholder="Name of Product" bind:value={product.name}>
    <input type="number" placeholder="No of Products" bind:value={product.quantity}>
    <input type="number" placeholder="Price of Products" bind:value={product.price}>

    <div>
        <button>Add Product</button>
    </div>
</form>

<style>
    form{
        display: flex;
        flex-direction: column;
        gap: 2rem;
        align-items: center;
    }
</style>