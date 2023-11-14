<script lang="ts">
  import * as Alert from "$lib/components/ui/alert";
</script>

<div>
    <div class="flex flex-col items-center justify-center h-[20rem]">
        <p class="font-bold text-3xl">Onix Client Script Downloader</p>
        <p class="font-semibold text-2xl">Click on the script you want to download.</p>

        <div class="w-[30rem] mt-4">
            <Alert.Root>
                <Alert.Title>Warning</Alert.Title>
    
                <Alert.Description>
                    Requires an Onix Client Patreon subscription.
                </Alert.Description>
            </Alert.Root>
        </div>
    </div>
</div>
