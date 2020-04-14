<template>
  <div>
    <h3>This is HelloWorld component</h3>
    <p>we got a lot to do here</p>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
  },
};
</script>
