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
  let copied = ref(false)
  const copyData = () =>{
    copied.value = true
    setTimeout(()=>{
      copied.value = false
    },1000)
  }

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
            <input type="text" placeholder="# No Ticket" class="bg-gray-200 w-96 rounded-lg border border-slate-500 px-4 py-2 outline-none" v-model.trim="source.ticket">
          </div>
          <div class="flex flex-col w-full">
            <span class="text-lg text-white font-semibold">Nama Kapal</span>
            <input type="text" placeholder="Nama Kapal" class="bg-gray-200 w-96 rounded-lg border border-slate-500 px-4 py-2 outline-none" v-model.trim="source.kapal">
          </div>
          <div class="flex flex-col w-full">
            <span class="text-lg text-white font-semibold">Nama Agent</span>
            <input type="text" placeholder="No Ticket" class="bg-gray-200 w-96 rounded-lg border border-slate-500 px-4 py-2 outline-none" v-model.trim="source.agent">
          </div>
          <div class="flex flex-col w-full">
            <span class="text-lg text-white font-semibold">PPK Inaportnet</span>
            <input type="text" placeholder="PPK Inaportnet" class="bg-gray-200 w-96 rounded-lg border border-slate-500 px-4 py-2 outline-none" v-model.trim="source.ppk">
          </div>
          <div class="flex flex-col w-full">
            <span class="text-lg text-white font-semibold">No PPKB</span>
            <input type="text" placeholder="No PPKB" class="bg-gray-200 w-96 rounded-lg border border-slate-500 px-4 py-2 outline-none" v-model.trim="source.ppkb">
          </div>
          <div class="flex flex-col w-full">
            <span class="text-lg text-white font-semibold">Permasalahan</span>
            <textarea placeholder="Permasalahan" class="bg-gray-200 w-96 rounded-lg border border-slate-500 px-4 py-2 outline-none" v-model.trim="source.desc" rows="4"></textarea>
          </div>
        </div>
        <div class="flex flex-col rounded-lg bg-slate-800 text-white px-6 py-4 w-[40rem] space-y-4">
          <div class="flex justify-between space-x-4">
            <button data-clipboard-target="#ticketData" class="bg-blue-500 cursor-pointer py-2 rounded-lg w-1/3 hover:bg-blue-600 active:bg-blue-700" id="clipboard" @click="copyData">
              Copy
            </button>
            <button v-if="copied" class="bg-green-400 rounded-lg text-white text-lg font-semibold text-center w-1/3 py-2">Copied</button>
            <button class="bg-red-500 cursor-pointer p-2 rounded-lg w-1/3 py-2" @click="reset">
              Reset
            </button>
          </div>
          <div id="ticketData">
            <table>
              <tbody class="flex flex-col text-left space-y-4">
                <tr>
                  <th class="capitalize w-40">nomor ticket</th>
                  <td class="w-2">:</td>
                  <td class="px-0">{{source.ticket}}</td>
                </tr>
                <tr>
                  <th class="capitalize w-40">nama kapal</th>
                  <td class="w-2">:</td>
                  <td class="px-0">{{source.kapal}}</td>
                </tr>
                <tr>
                  <th class="capitalize w-40">nama agent</th>
                  <td class="w-2">:</td>
                  <td class="px-0">{{source.agent}}</td>
                </tr>
                <tr>
                  <th class="uppercase w-40">ppk inaportnet</th>
                  <td class="w-2">:</td>
                  <td class="px-0">{{source.ppk}}</td>
                </tr>
                <tr>
                  <th class="uppercase w-40">ppkb</th>
                  <td class="w-2">:</td>
                  <td class="px-0">{{source.ppkb}}</td>
                </tr>
                <tr>
                  <th class="capitalize w-40">permasalahan</th>
                  <td class="w-2">:</td>
                  <td class="px-0">{{source.desc}}</td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
