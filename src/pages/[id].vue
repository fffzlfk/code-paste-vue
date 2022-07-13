<script setup lang="ts">
const { id } = defineProps<{ id: string }>()

const BASE_URL = 'http://localhost:8080/api'

interface Paste {
  id: string
  expired_at: string
  expired_days: number
  type: string
  data: string
}

let paste: Paste | null = $ref(null)

function fetchCode(id: string) {
  fetch(`${BASE_URL}/read/${id}`)
    .then(res => res.json())
    .then((res) => {
      paste = res
      console.log(paste)
    })
    .catch((err) => {
      console.error(err)
    })
}

const code = $computed(() => {
  if (paste)
    return paste.data

  return ''
})

onMounted(() => {
  fetchCode(id)
})
</script>

<template>
  {{ code }}
  <CodeEditor :code="code" />
</template>
