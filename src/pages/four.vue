<script setup lang="ts">
const personList = $ref([
  { name: '黄树光', phone: 13162610682 },
  { name: '黄树光', phone: 13162610681 },
])

const list = $ref([
  { position: '东门岗', persons: ['黄树光', '黄树光', '黄树光', '黄树光', '黄树光', '黄树光'] },
  { position: '中门岗', persons: ['黄树光', '黄树光', '黄树光', '黄树光', '黄树光'] },
  { position: '南门岗', persons: ['黄树光', '黄树光', '黄树光', '黄树光', '黄树光'] },
  { position: '小南门', persons: ['黄树光', '黄树光', '黄树光', '黄树光', '黄树光'] },
  { position: '监控室', persons: ['黄树光', '黄树光', '黄树光', '黄树光', '黄树光'] },
  { position: '机械车库', persons: ['黄树光', '黄树光', '黄树光', '黄树光', '黄树光'] },
  { position: '南门车场', persons: ['黄树光', '黄树光', '黄树光', '黄树光', '黄树光'] },
  { position: '机动岗', persons: ['黄树光', '黄树光', '黄树光', '黄树光', '黄树光'] },
  { position: '巡逻', persons: ['黄树光', '黄树光', '黄树光', '黄树光', '黄树光'] },
  { position: '二所', persons: ['黄树光', '黄树光', '黄树光', '黄树光', '黄树光'] },
])
</script>

<template>
  <div relative>
    <div flex flex-col divide-y h-full class="bg" text-2xl>
      <div font-700 leading-12 bg-red flex gap-5 justify-center px-3>
        当班人员信息
      </div>
      <div font-700 leading-10 bg="[rgba(186,0,0,0.29)]" flex gap-20 px-3>
        <div text="[red]">
          当班管理人员:
        </div>
        <div v-for="i in personList" :key="i.phone">
          {{ i.name }} （{{ i.phone }}）
        </div>
      </div>

      <div px-3 divide="y y-reverse dashed">
        <div text="[red]" font-500 my-1>
          (07:00-15:00) 岗位人员:
        </div>

        <div v-for="i in list" :key="i.position" grid="~ cols-[7rem_auto]" gap-10>
          <div font-500>
            {{ i.position }}
          </div>
          <div>
            {{ i.persons.join('，') }}
          </div>
        </div>
      </div>
    </div>
    <i class="i-my-bg2" absolute bottom-0 right-0 w-60 h-60 />
  </div>
</template>
