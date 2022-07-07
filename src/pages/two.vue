<script setup lang="ts">
const list = $ref([
  { name: '总控室', phone: 83035280, phone1: 83035280 },
  { name: '总控室', phone: 83035280 },
  { name: '总控室', phone: 83035280 },
  { name: '总控室', phone: 83035280 },
  { name: '总控室', phone: 83035280 },
  { name: '总控室', phone: 83035280, phone1: 83035280 },
  { name: '总控室', phone: 83035280 },
  { name: '总控室', phone: 83035280 },
  { name: '总控室', phone: 83035280 },
  { name: '总控室', phone: 83035280 },
  { name: '总控室', phone: 83035280 },
  { name: '总控室', phone: 83035280 },
  { name: '总控室', phone: 83035280 },
])
</script>

<template>
  <div flex flex-col h-full divide-y class="bg" text-2xl>
    <div font-700 leading-12 bg-red flex gap-5 justify-center px-3>
      常用通讯录
    </div>

    <div grid="~ cols-2" divide="x" flex-1>
      <div py-3 pr-8 divide="dashed y">
        <div v-for="i in list.slice(0, 8)" :key="i.name" grid="~ cols-[5rem_1fr_1fr]" gap-6 leading-12 px-3>
          <div>
            {{ i.name }}
          </div>
          <div justify-self-center>
            {{ i.phone }}
          </div>
          <div justify-self-end pr-3>
            {{ i.phone1 }}
          </div>
        </div>
        <div />
      </div>

      <div p-3 pl-8 flex="~ col">
        <div divide="dashed y">
          <div v-for="i in list.slice(8, -1)" :key="i.name" grid="~ cols-3" leading-12 px-3>
            <div>
              {{ i.name }}
            </div>
            <div justify-self-center>
              {{ i.phone }}
            </div>
            <div justify-self-end pr-3>
              {{ i.phone1 }}
            </div>
          </div>
          <div />
        </div>

        <div flex justify-between mt-auto>
          <div flex="~ col" justify-center>
            <i i-my-fire text-3xl />
            <div color-red-600 font-500 text-xl>
              火警: 119
            </div>
          </div>

          <div flex="~ col" justify-center>
            <i i-my-emergency text-3xl />
            <div color-rose-400 font-500 text-xl>
              急救: 120
            </div>
          </div>

          <div flex="~ col" justify-center>
            <i i-my-police text-3xl />
            <div color-blue-600 font-500 text-xl>
              匪警: 110
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
