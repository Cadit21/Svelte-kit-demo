<script lang="ts">
    import { PrivateKey } from '@bsv/sdk'
    
    let WIF:string
    let address:string
    
    function createkeys () {
    
    const privkey = PrivateKey. fromRandom()
    WIF = privkey.toWif()
    console. log("Priyate Key WIF format is ", WIF)
    address = privkey. toAddress()
    console. log("Your bitcoin address is ", address)
    }
    
    </script>
    
    <section>
    <button class="bg-black text-white p-2 mx-3 rounded" on:click={createkeys}> Generate New Wallet Keys </button>
    <p class="mx-3">Private Key WIF format is {WIF}</p>
    <p class="mx-3"> Your BitCoin Address is {address}</p>
    </section>