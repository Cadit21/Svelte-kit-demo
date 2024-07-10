<script lang="ts">
    import { PrivateKey } from '@bsv/sdk';
    
    let WIF: string;
    let address: string;
    
    function createkeys() {
        const privkey = PrivateKey.fromRandom();
        WIF = privkey.toWif();
        console.log("Private Key WIF format is", WIF);
        address = privkey.toAddress().toString();
        console.log("Your Bitcoin address is", address);
    }
</script>


<section class="container mx-auto p-6 align-middle w-96 my-20 bg-slate-300">
    <div class="text-center">
        <button  on:click={createkeys} class="bg-blue-500 text-white p-4 rounded shadow-md hover:bg-blue-700 transition duration-300" >Generate New Wallet Keys</button>
    </div>
    <div class="mt-6 p-6 bg-white rounded shadow-md">
        <p class="text-lg font-semibold">Private Key WIF format is:</p>
        <p id="wif" class="text-xl text-gray-700 mt-2 break-all">{WIF}</p>
    </div>
    <div class="mt-6 p-6 bg-white rounded shadow-md">
        <p class="text-lg font-semibold">Your Bitcoin Address is:</p>
        <p id="address" class="text-xl text-gray-700 mt-2 break-all">{address}</p>
    </div>
</section>

