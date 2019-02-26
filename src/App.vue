<template>
  <div id="app">
    <button @click="transfer"> getMappedTokenAddress </button>
  </div>
</template>

<script>

import Matic from 'maticjs';
import config from './config'

export default {
    data() {
      return {
      }
    },
    methods: {
        transfer() {
        let tokenAddress = "0xc4375b7de8af5a38a93548eb8453a498222c4ff2";

        const from = '0x7C27C62376f85797288b4Cc2B5b924d2FE70a462' // from address
        const to = '0xc15d8950f6a98dc1708200b1ad368c95d3990ecb' // to address

        const token = '0xdda2b0cea46316192fb440611acc1b36dd16f49f' // test token address
        const newAmount = '4000000000000000000' // amount in wei
        
        console.log(config.MATIC_PROVIDER)
        // Create object of Matic
        const matic = new Matic({
          maticProvider: config.MATIC_PROVIDER,
          parentProvider: config.PARENT_PROVIDER,
          rootChainAddress: config.ROOTCHAIN_ADDRESS,
          syncerUrl: config.SYNCER_URL,
          watcherUrl: config.WATCHER_URL,
          maticWethAddress: config.MATICWETH_ADDRESS,
        })

        matic.wallet = '0x' + config.privateKey // prefix with `0x`

      matic
  .getMappedTokenAddress("0xC4375B7De8af5a38a93548eb8453a498222C4fF2")
  .then(address => {
    console.log("matic address", address)
  })},
    },
    mounted() {

    }
  }
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
