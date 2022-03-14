<script>
    export let name, age, favoriteColor = "white";
</script>

<p style="background-color: {favoriteColor}">
    {#if age}
        {name === "Thor" ? "I'm" : name + " is"} {age} years old.
    {:else}
        Im not sure how old {name} is.
    {/if}
    <br>
    {name === "Thor" ? "My" : name + "'s"} favorite color is {favoriteColor}.
</p>

<style>
    p{
        width: fit-content;
        padding: 10px;
        position: relative;
        transform: translate(-50%, 0);
		left: 50%;
        font-weight: bold;
        border-radius: 20px;
        border: 2px solid black;
        margin: 0;
    }
</style>