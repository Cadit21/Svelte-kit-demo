<script>
    export let names;
    let edit = false;

    function handleChange() {
        edit = !edit;
    }
</script>

<div class="mt-10 pt-10 w-full max-w-xl p-12 mx-auto rounded-lg shadow-xl dark:bg-white/10 bg-white/30 ring-1 ring-gray-900/5 backdrop-blur-lg">
    <div class="flex items-center justify-between mb-4">
        <div class="space-y-1">
            <h2 class="text-xl font-semibold">List of Users</h2>
            <p class="text-sm text-gray-500">
                Fetched {names.length} users
            </p>
        </div>
    </div>
    <div class="divide-y divide-gray-900/5">
        {#each names as user (user.id)}
            <div class="flex items-center justify-between py-3">
                <div class="flex items-center space-x-4">
                    <div class="flex">
                        <p class="font-medium pt-1 leading-none">{user.name}</p>
                        <p class="font-medium pl-5 text-gray-500 pt-0">{user.email}</p>
                    </div>
                </div>
                <div class="flex items-center space-x-4" >
                    {#if !edit}
                        <button on:click={handleChange} class=" bg-green-500 hover:bg-blue-700 text-white rounded px-2 py-1" >
                            Update
                        </button>
                    {:else}
                        <form method="POST" action="/profiles?/update">
                            <input type="hidden" name="id" value={user.id}/>
							
                            <input type="text" name="email" placeholder="New email" class="w-full sm:w-1/2 border rounded-lg px-2 mx-1 " required>
							
							<button type="submit" class="bg-green-500 text-white px-3 py-1 rounded">
                                Save
                            </button>
                            <button type="button" on:click={handleChange} class="bg-red-500 text-white px-2 py-1 rounded">
                                Cancel
                            </button>
							
							
                        </form>
                    {/if}
                    
                    <form method="POST" action="/profiles?/delete">
                        <input type="hidden" name="id" value={user.id}>
                        <button type="submit">
                            <img class="w-4 float-right" src="./trash-can.svg" alt="delete"/>
                        </button>
                    </form>
                </div>
            </div>
        {/each}
    </div>
</div>
