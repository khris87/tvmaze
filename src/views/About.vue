<template>
  <div class="about">
    <h1>This is an about my contacts page</h1>
    <div class="container"><hr class="my-5"><Contacts /></div>
  </div>
</template>

<script>
  // @ is an alias to /src
  // import HelloWorld from '@/components/HelloWorld.vue';
  import Contacts from "../components/Contacts";

export default {
  name: 'about my contacts',
  components: {
    Contacts
  }
}

</script>