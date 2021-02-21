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

   function changeText(event) {
      qrcode.clear();
      qrcode.makeCode(event.target.value);
   }
</script>

<div class="container">
   <h1 class="heading">Create QRCode</h1>

   <div id="qrcode" />

   <input
      type="text"
      autocomplete="off"
      spellcheck="false"
      class="input__text"
      on:input={changeText}
      placeholder="your text...."
   />

   <a href="/#" class="download__button">Download QRCode</a>
</div>

<style>
   .container {
      width: 88%;
      margin: 70px auto;
      text-align: center;
   }

   .heading {
      padding: 15px;
      font-size: 1.7rem;
      font-weight: bold;
      text-align: center;
      margin-bottom: 50px;
      border-radius: 10px;
      letter-spacing: 1.4px;
      display: inline-block;
      background-color: #ffffff;
      border: 2px solid #000000;
      box-shadow: 8px 8px 0.6px #000000;
   }

   #qrcode {
      width: 94%;
      margin: auto;
      display: flex;
      padding: 30px;
      cursor: pointer;
      border-radius: 10px;
      justify-content: center;
      border: 3px solid #000000;
      background-color: #ffffff;
      box-shadow: 12px 12px 0.6px #000000;
      transition: box-shadow 0.1s, transform 0.1s;
   }

   #qrcode:hover {
      transform: translateX(3px);
      box-shadow: 4px 4px 0.6px #000000;
   }

   .input__text {
      width: 100%;
      padding: 12px;
      outline: none;
      margin-top: 60px;
      font-size: 1.3rem;
      border-radius: 6px;
      border: 2px solid #000000;
      background-color: #ffffff;
      box-shadow: 6px 6px 0.6px #000000;
      transition: box-shadow 0.1s, transform 0.1s;
   }

   .input__text::placeholder {
      font-weight: bold;
   }

   .input__text:focus {
      transform: translateX(3px);
      box-shadow: 2px 2px 0.6px #000000;
   }

   .download__button {
      padding: 15px;
      color: #000000;
      margin-top: 50px;
      font-size: 1.2rem;
      border-radius: 10px;
      letter-spacing: 1px;
      display: inline-block;
      text-decoration: none;
      background-color: #ffffff;
      border: 2px solid #000000;
      box-shadow: 7px 7px 0.6px #000000;
      transition: box-shadow 0.1s, transform 0.1s;
   }

   .download__button:hover {
      transform: translateX(3px);
      box-shadow: 3px 3px 0.6px #000000;
   }

   @media screen and (min-width: 580px) {
      .container {
         width: 75%;
      }
   }

   @media screen and (min-width: 705px) {
      .container {
         width: 70%;
      }
   }

   @media screen and (min-width: 840px) {
      #qrcode {
         width: 70%;
      }
   }

   @media screen and (min-width: 1040px) {
      .container {
         width: 66%;
      }
   }

   @media screen and (min-width: 1140px) {
      #qrcode {
         width: 65%;
      }
   }

   @media screen and (min-width: 1330px) {
      .container {
         width: 60%;
      }
   }

   @media screen and (min-width: 1490px) {
      .container {
         width: 50%;
      }
   }

   @media screen and (min-width: 1660px) {
      #qrcode {
         width: 55%;
      }
   }

   @media screen and (min-width: 1860px) {
      .container {
         width: 43%;
      }
   }
</style>
