<template>
  <section>
    <div class="setting">
      <div class="text">
        <div class="title">ღამის რეჟიმი / Dark Mode</div>
      </div>
      <div class="control">
        <Toggle v-model="darkMode" @click="darkModeClick" />
      </div>
    </div>
    <div class="setting">
      <div class="text">
        <div class="title">ფერის ბრმა რეჟიმი / Color Blind Mode</div>
        <div class="description">მაღალი კონტრასტის ფერები</div>
      </div>
      <div class="control">
        <Toggle v-model="colorBlind" @click="colorBlindClick"/>
      </div>
    </div>
    <div class="setting" id="footnote">
      <div class="text">
        <div class="title">ჩვენი სერვისები</div>
      </div>
      <div class="control">
        <p><a href="https://any.ge/">ონლაინ სერვისები</a></p>
        <p><a href="https://neverhaveiever.online/">Never Have I Ever Questions</a></p>
        <p><a href="https://frameworkscatalog.com/">Frameworks Catalog</a></p>
        <p><a href="https://ergaleia.net/">Free Online Web Tools For You</a></p>
      </div>
    </div>
  </section>
</template>
<script setup lang="ts">
  import Toggle from '@vueform/toggle'

  let darkMode = $ref(!localStorage.getItem("darkMode") || localStorage.getItem("darkMode") == "true");
  let colorBlind = $ref(localStorage.getItem("colorBlind") == "true")

  function darkModeClick(){
    localStorage.setItem("darkMode",darkMode)

    document.body.className = `${darkMode ? 'nightmode' : ""} ${colorBlind ? 'colorblind' : ""}`;
  }

  function colorBlindClick(){
    localStorage.setItem("colorBlind",colorBlind)

    if(!colorBlind) {
      document.body.className = darkMode ? " nightmode" : "";
    } else {
      document.body.className = document.body.className + " colorblind";
    }
  }
 
</script>

<style src="@vueform/toggle/themes/default.css"></style>
<style scoped>

  .setting {
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 1px solid var(--color-tone-4);
    padding: 16px 0;
  }

  a, a:visited {
    color: var(--color-tone-2);
  }

  .title {
    font-size: 18px;
  }
  .text {
    padding-right: 8px;
  }
  .description {
    font-size: 12px;
    color: var(--color-tone-2);
  }

  #footnote {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    padding: 10px 32px;
    color: var(--color-tone-2);
    font-size: 14px;
    text-align: right;
    display: flex;
    justify-content: space-between;
    align-items: flex-end;
  }

  #privacy-policy,
  #copyright {
    text-align: left;
  }

  @media only screen and (min-device-width : 320px) and (max-device-width : 480px) {
    .setting {
      padding: 16px;
    }
  }

  
</style>