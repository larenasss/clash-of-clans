<template>
  <div class="one-third">
      <div class="stat-value">
        {{ value }}
      </div>
      <div class="stat">
        {{ title }}
      </div>
    </div>
</template>

<script>
  export default {
    props: {
      title: {
        type: String,
        required: true,
      },
      value: {
        type: String,
        required: true,
      },
    }
  }
</script>