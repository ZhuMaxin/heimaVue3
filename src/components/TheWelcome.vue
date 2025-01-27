<script setup>
import { ref, useTemplateRef, reactive, onMounted, computed, watch, inject } from 'vue'
const props = defineProps({
  msg: String,
  xypreactive: Object,
  xypref: Number,
})
const emit = defineEmits(['chnagexypref'])

const num = ref(0)

onMounted(()=>{
  const btnAReactive = useTemplateRef('btnAReactive')
  console.log(btnAReactive);
})

const nReactive = reactive({ count: 0 })
function add() {
  num.value++
}
const aReactive = () => nReactive.count++

const szList = ref([1, 2, 3, 4])
const szList2 = computed(() => szList.value.filter((n) => n > 2))

watch(num, (newValue) => {
  szList.value.push(newValue)
})

const wrefo = ref('cccc')
const wreco = reactive({ aaa: 0 })
watch(wrefo, (newValue) => {
  console.log('watch ref', newValue)
})
watch(wreco, (newValue) => {
  console.log('watch reactive', newValue)
})
watch(props.xypreactive, (newValue) => {
  console.log('watch xypreactive', newValue)
})
watch(
  () => props.xypref,
  (newValue) => {
    console.log('watch xypref', newValue)
  },
)
setTimeout(() => {
  wrefo.value = 'vvv'
  wreco.aaa++
}, 2000)
setTimeout(() => {
  emit('chnagexypref', 200)
}, 4000)

defineExpose({
  num,
  nReactive
})

const injectxx = inject('injectxx')
const injectFunAdd = inject('injectFunAdd')
</script>

<template>
  <el-button type="success" plain>Success</el-button>
  <h1>{{ msg }}</h1>
  <div>{{ xypreactive.ks }}</div>
  <button @click="add">{{ num }}</button>
  <button ref="btnAReactive" @click="aReactive">{{ nReactive.count }}</button>
  <div>原数组{{ szList }}</div>
  <div>计算属性数组{{ szList2 }}</div>
  <div>inject数据</div>
  <div>{{ injectxx }}</div>
  <button @click="injectFunAdd(1)">inject+1</button>
</template>
