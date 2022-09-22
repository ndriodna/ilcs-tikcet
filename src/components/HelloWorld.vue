<script setup>
  import { reactive, ref, watchEffect } from 'vue'

  const source = reactive({
    ticket: '',
    kapal: '',
    ppk: '',
    agent: '',
    ppkb: '',
    desc: '',
  })
  const copied = ref(false)
  const copy = () =>{
    copied.value = true
    setTimeout(()=>{
      copied.value = false
    },2000)
  }
  watchEffect(()=>{
    copied.value
  })
  const reset = () =>{
    source.ticket = ''
    source.kapal = ''
    source.ppk = ''
    source.agent = ''
    source.ppkb = ''
    source.desc = ''
  }

</script>

<template>
  <div class="mx-auto container h-screen ">
    <div class="flex justify-center px-6 py-4">
      <div class="flex justify-between space-x-4 py-12">
        <div class="space-y-2">
          <div class="flex flex-col w-full">
            <span class="text-lg text-white font-semibold">No Ticket</span>
            <input type="text" placeholder="# No Ticket" class="bg-gray-200 w-96 rounded-lg border border-slate-500 px-4 py-2 outline-none" v-model="source.ticket">
          </div>
          <div class="flex flex-col w-full">
            <span class="text-lg text-white font-semibold">Nama Kapal</span>
            <input type="text" placeholder="Nama Kapal" class="bg-gray-200 w-96 rounded-lg border border-slate-500 px-4 py-2 outline-none" v-model="source.kapal">
          </div>
          <div class="flex flex-col w-full">
            <span class="text-lg text-white font-semibold">PPK Inaportnet</span>
            <input type="text" placeholder="PPK Inaportnet" class="bg-gray-200 w-96 rounded-lg border border-slate-500 px-4 py-2 outline-none" v-model="source.ppk">
          </div>
          <div class="flex flex-col w-full">
            <span class="text-lg text-white font-semibold">No Ticket</span>
            <input type="text" placeholder="No Ticket" class="bg-gray-200 w-96 rounded-lg border border-slate-500 px-4 py-2 outline-none" v-model="source.agent">
          </div>
          <div class="flex flex-col w-full">
            <span class="text-lg text-white font-semibold">No PPKB</span>
            <input type="text" placeholder="No PPKB" class="bg-gray-200 w-96 rounded-lg border border-slate-500 px-4 py-2 outline-none" v-model="source.ppkb">
          </div>
          <div class="flex flex-col w-full">
            <span class="text-lg text-white font-semibold">Permasalahan</span>
            <textarea placeholder="Permasalahan" class="bg-gray-200 w-96 rounded-lg border border-slate-500 px-4 py-2 outline-none" v-model="source.desc"></textarea>
          </div>
        </div>
        <div class="flex flex-col rounded-lg bg-slate-800 text-white px-6 py-4 w-[32rem] space-y-4">
          <div v-if="copied" class="flex bg-green-400 rounded-lg justify-center">
            <div class="text-white text-lg font-semibold text-center px-12 py-2">Copied</div>
          </div>
          <div class="flex justify-start space-x-4">
            <button data-clipboard-target="#data" class="bg-blue-500 cursor-pointer p-2 rounded-lg w-1/3 hover:bg-blue-600 active:bg-blue-700" id="clipboard" @click="copied()">
              Copy
            </button>
            <button class="bg-red-500 cursor-pointer p-2 rounded-lg w-1/3" @click="reset">
              Reset
            </button>
          </div>
          <div class="flex space-y-2">
            <div class="flex"></div>
          </div>
          <table id="data">
            <tbody >
              <tr>
                <td class="capitalize">nomor ticket</td>
                <td class="">:</td>
                <td class="w-full break-all capitalize">{{source.ticket}}</td>
              </tr>
              <tr>
                <td class="capitalize">nama kapal</td>
                <td class="">:</td>
                <td class="w-full break-all capitalize">{{source.kapal}}</td>
              </tr>
              <tr>
                <td class="capitalize">ppk inaportnet</td>
                <td class="">:</td>
                <td class="w-full break-all capitalize">{{source.ppk}}</td>
              </tr>
              <tr>
                <td class="capitalize">nama agent</td>
                <td class="">:</td>
                <td class="w-full break-all capitalize">{{source.agent}}</td>
              </tr>
              <tr>
                <td class="">No PPKB</td>
                <td class="">:</td>
                <td class="w-full break-all capitalize">{{source.ppkb}}</td>
              </tr>
              <tr>
                <td class="capitalize">permasalahan</td>
                <td class="">:</td>
                <td class="w-full break-all capitalize">{{source.desc}}</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>
