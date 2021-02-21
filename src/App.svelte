<script>
   import { onMount } from "svelte";
   import { scale, fade } from "svelte/transition";

   let qrcode;
   let downloadButton;
   let qrcodeContainer;
   let qrcodeValue = "";

   onMount(() => {
      qrcode = new QRCode(document.getElementById("qrcode"), {
         text: "https://twitter.com/calon_jenazah__",
         width: 250,
         height: 250,
         colorDark: "#000000",
         colorLight: "#ffffff",
         correctLevel: QRCode.CorrectLevel.H,
      });
   });

   function changeText(event) {
      if (qrcodeValue !== "") {
         qrcode.clear();
         qrcode.makeCode(event.target.value);
         downloadButton.href = qrcodeContainer.childNodes[1].src;
      } else {
         qrcode.clear();
         qrcode.makeCode(qrcodeValue);
      }
   }
</script>

<div class="container">
   <h1 class="heading">Create QRCode</h1>

   <div id="qrcode" bind:this={qrcodeContainer} />

   <input
      type="text"
      autocomplete="off"
      spellcheck="false"
      class="input__text"
      on:input={changeText}
      bind:value={qrcodeValue}
      placeholder="your text...."
   />

   {#if qrcodeValue !== ""}
      <a
         href="/#"
         download="qrcode"
         class="download__button"
         in:scale={{ duration: 300 }}
         out:fade={{ duration: 150 }}
         bind:this={downloadButton}>Download QRCode</a
      >
   {/if}
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
      margin-bottom: 60px;
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
      border-radius: 10px;
      justify-content: center;
      border: 3px solid #000000;
      background-color: #ffffff;
      box-shadow: 12px 12px 0.6px #000000;
      transition: box-shadow 0.1s, transform 0.1s;
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

   @media screen and (min-width: 840px) {
      #qrcode {
         width: 70%;
      }
   }

   @media screen and (min-width: 1140px) {
      #qrcode {
         width: 65%;
      }
   }

   @media screen and (min-width: 1660px) {
      #qrcode {
         width: 55%;
      }
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

   @media screen and (min-width: 1040px) {
      .container {
         width: 66%;
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

   @media screen and (min-width: 1860px) {
      .container {
         width: 43%;
      }
   }
</style>
