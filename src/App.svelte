<script>
   import { onMount } from "svelte";

   let qrcode;

   onMount(() => {
      qrcode = new QRCode(document.getElementById("qrcode"), {
         text: "https://github.com/apriliandi246",
         width: 228,
         height: 228,
         colorDark: "#000000",
         colorLight: "#ffffff",
         correctLevel: QRCode.CorrectLevel.H,
      });
   });
</script>

<h1>Hello World</h1>

<div id="qrcode" />

<style>
   h1 {
      color: rgb(0, 102, 192);
   }
</style>
