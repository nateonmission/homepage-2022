<template>
  <div class="who">
    <div class="avatar">
      <img
        src="../../public/imgs/nateonmission.jpg"
        alt="Nate On Mission"
        class="avatar"
      />
    </div>
    <div class="name">
      <p class="slackey_emphisis">{{ handle }}</p>
    </div>
    <div class="intro">
      <p class="intro normal">
        Hi, my name is Nate Allen and I'm a software developer and technologist!
        I've been playing with computers since I was 8 years old, when I got a
        Commodor64 for Christmas! Over the years, I've seen many changes and
        have enjoyed the ride as technology changes and conventions come and go.
      </p>
    </div>
  </div>
</template>

<script>
export default {
  props: ["handle"],
};
// This is where your Javascript goes
// to define your Vue component, which
// can be a Layout, a Page or your own
// component used throughout the app.
</script>

<style>
/* This is where your CSS goes */
</style>
