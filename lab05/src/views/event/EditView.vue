<script setup lang="ts">
import { toRefs, defineProps } from 'vue'
import { type Event } from '@/types'
import { useMessageStore } from '@/stores/message'
import { useRouter } from 'vue-router'
const store = useMessageStore()
const router = useRouter()
const props = defineProps<{
  event: Event
  id: number
}>()
const { event } = toRefs(props)
const handleEdit = () => {
  store.updateMessage('Event data has been successfully updated')
  setTimeout(() => {
    store.resetMessage()
  }, 3000)
  router.push({ name: 'event-detail-view', params: { id: props.id } })
}
</script>

<template>
  <p>Edit event here</p>
  <button @click="handleEdit">Save Changes</button>
</template>
