<script setup lang=ts>
const list = $ref([
  { content: '深圳市，珠海市的来（反）佛人员必须持有48小时内核酸阴性结果证明。', color: 'text-[red]' },
  { content: '深圳市，珠海市的来（反）佛人员必须持有48小时内核酸阴性结果证明。' },
  { content: '深圳市，珠海市的来（反）佛人员必须持有48小时内核酸阴性结果证明。' },
  { content: '深圳市，珠海市的来（反）佛人员必须持有48小时内核酸阴性结果证明。' },
  { content: '深圳市，珠海市的来（反）佛人员必须持有48小时内核酸阴性结果证明。' },
  { content: '深圳市，珠海市的来（反）佛人员必须持有48小时内核酸阴性结果证明。' },
  { content: '深圳市，珠海市的来（反）佛人员必须持有48小时内核酸阴性结果证明。' },
])
</script>

<template>
  <div flex flex-col h-full divide-y class="bg">
    <div text-xl font-700 leading-12 bg-red flex gap-5 justify-center px-3>
      疫情防控重点关注城市
    </div>

    <div grid="~ cols-2" divide="x" flex-1>
      <div v-for="index in [0, 1]" :key="index" px-7 pt-4 gap-3 flex="~ col">
        <div
          v-for="(i, ind) in list.slice(index, index + 3)"
          :key="ind"
          px-3 py-5 min-h-32 text-2xl
          class="item "
          :class="i.color"
        >
          {{ i.content }}
        </div>
      </div>
    </div>
  </div>
</template>

<style>
.item{
  background: linear-gradient(135deg, rgba(16,16,16,0.31) 0%, rgba(255,255,255,0.4) 100%);
  box-shadow: inset -4px -4px 4px 0 rgba(43,43,43,0.72), inset 4px 4px 4px 0 rgba(174,174,174,0.48);
}
</style>
