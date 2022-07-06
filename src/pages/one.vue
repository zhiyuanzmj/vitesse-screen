<script lang="ts" setup>
import dayjs from 'dayjs'

const { data } = useFetch('https://devapi.qweather.com/v7/weather/3d?location=101280805&key=dcc5d99ad3e44bf69a6eb73664d6caea').json()
const { data: now } = useFetch('https://devapi.qweather.com/v7/weather/now?location=101280805&key=dcc5d99ad3e44bf69a6eb73664d6caea').json()
const row = $computed(() => ({
  ...data.value?.daily[0],
  ...now.value?.now,
  weakDay: ['周末', '周一', '周二', '周三', '周四', '周五', '周六'][dayjs().day()],
  time: dayjs().format('HH:MM'),
}))
</script>

<template>
  <div text-2xl font-700 leading-15 bg-red flex gap-5 justify-between px-3>
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
      <span>{{ row.time }}</span>
    </div>
  </div>
  <div>13</div>
</template>
