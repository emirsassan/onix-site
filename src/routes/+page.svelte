<script lang="ts">
    import Hero from "../includes/Hero.svelte";
    import ModCard from "../includes/ModCard.svelte";
    import Navbar from "../includes/Navbar.svelte";
    import { onMount } from "svelte";

    type IMod = {
        name: string;
        description: string;
        url: string;
    }

    let data: Array<IMod> = [];

    onMount(async () => {
        const a = await fetch("https://raw.githubusercontent.com/OnixClient-Scripts/OnixClient_Scripts/master/index.json")
        const b = await a.json()

        data = b.modules
    })
</script>

<div>
    <div>
        <Navbar />
    </div>

    <div>
        <Hero />

        <div class="m-4">
            <hr />
        </div>
    </div>

    <div>
        <ModCard mods={data} />
    </div>
</div>