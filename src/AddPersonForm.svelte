<script>
    // svelte imports here
	import {createEventDispatcher} from "svelte";

    let dispatch = createEventDispatcher();
    let name;
    let beltColour;
    let age;
    let skills = [];

    const handleSubmit = () =>{
        const person = {
            name:name,
            beltColour: beltColour,
            age:age,
            skills:skills,
            id:Math.random()
        }
        dispatch("addPerson", person);
    }

    
    </script>

<form on:submit|preventDefault={handleSubmit}>
    <input
    type ="text"
    placeholder="name"
    bind:value={name}
    />
    <input
    type ="number"
    placeholder="Age"
    bind:value={age}
    />
    <label>Skills:</label>
    <input type ="checkbox" bind:group={skills} value="fighting"> Fighting <br>
    <input type ="checkbox" bind:group={skills} value ="sneaking"> Sneaking <br>
    <input type ="checkbox" bind:group={skills} value="running"> Running <br>

    <select bind:value={beltColour}>
        <option value ="black">black</option>
        <option value ="orange">orange</option>
        <option value ="brown">brown</option>
        <option value ="white">white</option>
    </select>

    <button>Add Person</button>
</form>

<style>

</style>

