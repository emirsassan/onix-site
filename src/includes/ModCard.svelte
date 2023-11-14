<script lang="ts">
  import * as Card from "$lib/components/ui/card";
  import Button from "$lib/components/ui/button/button.svelte";
  import {
    Popover,
    PopoverTrigger,
    PopoverContent
  } from "$lib/components/ui/popover";

  export let mods: any;

  async function downloadScript(thing: string) {
    const data = await fetch("https://raw.githubusercontent.com/OnixClient-Scripts/OnixClient_Scripts/master/Modules/" + thing as string) //funny code
    const b = await data.text()

    return `data:text/plain;charset=utf-8,${encodeURIComponent(b)}`
  }
</script>

<div class="mx-2 my-2">
    <div class="grid grid-cols-5 gap-5">
        {#each mods as shit}
            <Card.Root>
                <Card.Header>
                    <Card.Title>
                        {shit.name}
                    </Card.Title>
                </Card.Header>
    
                <Card.Content>
                    <p>{shit.description}</p>
                </Card.Content>
    
                <Card.Footer class="flex justify-self-end">
                    <Popover portal={null}>
                        <PopoverTrigger asChild let:builder>
                          <Button builders={[builder]} variant="outline">Actions</Button>
                        </PopoverTrigger>
                        <PopoverContent class="w-80">
                          <div class="grid gap-4">
                            <div class="space-y-2">
                              <h4 class="font-medium leading-none">Controls</h4>
                              <p class="text-sm text-muted-foreground">
                                Select the action
                              </p>
                            </div>
                            <div class="grid gap-2">
                              <div class="grid grid-cols-3 items-center gap-4">
                                <Button variant="outline" href={shit.url}>View</Button>
                                <Button download={shit.file} href={`${downloadScript(shit.file)}`}>Download</Button>
                              </div>
                            </div>
                          </div>
                        </PopoverContent>
                      </Popover>
                </Card.Footer>
            </Card.Root>
        {/each}
    </div>
</div>
