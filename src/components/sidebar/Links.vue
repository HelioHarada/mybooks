<template>
  <div>
    <q-item clickable v-ripple :to="{path : router}" >
      <q-item-section avatar>
        <q-icon :name="icon" />
      </q-item-section>
      <q-item-section>
        {{title}}
      </q-item-section>
    </q-item>
  </div>
</template>
<script>
export default {
  props: {
    title: {
      type: String
    },
    router: {
      type: String,
      default: '#'
    },
    icon: {
      type: String
    }
  }
}
</script>
