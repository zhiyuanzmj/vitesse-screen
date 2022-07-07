<script lang="ts" setup>
import dayjs from 'dayjs'

const { data } = useFetch('https://devapi.qweather.com/v7/weather/3d?location=101280805&key=dcc5d99ad3e44bf69a6eb73664d6caea').json()
const { data: now } = useFetch('https://devapi.qweather.com/v7/weather/now?location=101280805&key=dcc5d99ad3e44bf69a6eb73664d6caea').json()
const row = $computed(() => ({
  ...data.value?.daily[0],
  ...now.value?.now,
  weakDay: ['周末', '周一', '周二', '周三', '周四', '周五', '周六'][dayjs().day()],
}))
let time = $ref('')
setInterval(() => { time = dayjs().format('HH:mm:ss') }, 1000)

const parkList = $ref([
  { name: '信访局', count: 23, total: 40 },
  { name: '机械车库', count: 224, total: 20, class: 'text-[red]' },
  { name: '新能源', count: 21, total: 50 },
  { name: '小南门', count: 23, total: 41 },
  { name: '机械东门', count: 11, total: 40 },
  { name: '园内', count: 23, total: 22 },
])

const doorList = $ref([
  { name: '东门', count: 22 },
  { name: '南门', count: 25 },
  { name: '西门', count: 221 },
])
</script>

<template>
  <div flex flex-col h-full divide-y class="bg" text-2xl>
    <div font-700 leading-12 bg-red flex gap-5 justify-between px-3>
      <div><i class="i-my-position" />禅城区</div>
      <div flex gap-2>
        <i :class="`i-my-${row.icon}-fill`" />
        <span>{{ row.temp }}°C</span>
        <span>{{ row.text }}</span>
      </div>

      <div>
        (最高{{ row.tempMax }}°C / 最低{{ row.tempMin }}°C)
      </div>

      <div flex gap-3>
        <span>{{ row.fxDate }}</span>
        <span>{{ row.weakDay }}</span>
        <span w-21>{{ time }}</span>
      </div>
    </div>

    <div grid="~ cols-2" divide="x" flex-1>
      <div p-7 divide="dashed y y-reverse">
        <div bg-neutral-600 rounded flex justify-between px-3 py-2 font-500 mb-3>
          <div>停车场</div>
          <div>剩余位</div>
          <div>总车位</div>
        </div>
        <div v-for="i in parkList" :key="i.name" grid="~ cols-3" leading-12 px-3>
          <div :class="i.class">
            {{ i.name }}
          </div>
          <div justify-self-center :class="i.class">
            {{ i.count }}
          </div>
          <div justify-self-end pr-3 :class="i.class">
            {{ i.total }}
          </div>
        </div>
      </div>
      <div relative>
        <div p-7 divide="dashed y y-reverse">
          <div bg-neutral-600 rounded flex justify-center px-3 py-2 font-500 mb-3>
            各岗门来访登记数
          </div>
          <div v-for="i in doorList" :key="i.name" grid="~ cols-2" leading-12 px-3>
            <div>
              {{ i.name }}
            </div>
            <div justify-self-end pr-3>
              {{ i.count }}
            </div>
          </div>
        </div>
        <i class="i-my-bg1" absolute right-5 bottom-0 w-xs h-xs />
      </div>
    </div>
  </div>
</template>
