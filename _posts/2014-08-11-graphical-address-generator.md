---
title: Graphical Address Generator
js: 
  - /js/btc.min.js
  - /js/wallet-gen.js 
css: 
  - /css/wallet-gen.css
excerpt: <p>Observe el funcionamiento interno de una dirección bitcoin.</p>
image: /assets/imgs/thumbs/gen-addr.png
---

<div>Esto fue construido con fines académicos. Si desea una dirección segura, lea <a href="https://en.bitcoin.it/wiki/Paper_wallet" target="_blank">this.</a></div>
<div class="private">
<h2 class="section-header">Generar clave privada</h2>
<div class="private-key">
  <div class="container">
    <input id="passphrase" type="text" name="passphrase" placeholder="Escriba la contraseña aquí...">
    <div>
      <img src="/assets/imgs/wallet-gen/sha-expand.svg" />
    </div>
    <div class="hex-container hex-padding pk"></div>
    <div class="information information-arrow-left-bottom step1"><span class="title">1.</span>La clave privada es de 256 bits aleatorios.</div>
  </div>
</div>

<div class="wif-container">
  <div>
    <div class="container">
      <div class="hex-container">
        <div class="version hex-left">80</div>
        <div class="pk hex-middle"></div>
        <div class="compression-flag hex-middle">01</div>
        <div class="checksum-pk checksum hex-right"></div>
      </div>
      <div class="information step2 information-arrow-bottom-left"><span class="title">2.</span> Anteponer el número de versión.</div>
      <div class="information step3 information-arrow-bottom-right"><span class="title">3.</span> Anteponer el número de versión.</div>
      <div class="information step4 information-arrow-bottom-left"><span class="title">4.</span> Anexar suma de comprobación. La suma de verificación son los primeros 4 bytes del hash sha256 doble de lo que sea que se esté revisando.</div>
    </div>
  </div>

  <div>
    <div class="container">
      <img src="/assets/imgs/wallet-gen/base58-wif.svg" />
      <div>
        <div class="private-wif hex-container hex-padding"></div>
      </div>
      <div class="information information-arrow-left-top step5"><span class="title">5.</span> Los datos codificados en Base58 son más fáciles de leer y administrar. Las "flechas dobles" indican que esto es reversible.</div>
    </div>
  </div>
</div>
</div>

<div class="public">
<h2 class="section-header">Generar clave pública</h2>
<div class="public-equation">
  <div class="pub-key-label">k</div> = <span class="hex-container hex-padding pk"></span> * 
  <img src="/assets/imgs/wallet-gen/elliptic-curve.gif" />
  <div class="information information-arrow-left-top step6"><span class="title">6.</span> Multiplique la clave privada por el punto generador de curva elíptica para obtener la clave pública. La clave pública es un punto en la curva elíptica y tiene coordenadas xey.
  </div>
</div>

<div>
  <div class="container">
    <img class="public-key-split" src="/assets/imgs/wallet-gen/public-graphic.svg" />
    <div class="public-coords">
      <div class="public-coord-x">
        x = <span class="hex-container hex-padding public-x"></span>
      </div>
      <div class="public-coord-y">
        y = <span class="hex-container hex-padding public-y"></span><span class="public-y-even-odd"></span>
      </div>
    </div>
  </div>
</div>

<div class="public-key">
<div>
  <svg version="1.1" id="parity-arrow" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
    width="568.875px" height="75px" viewBox="0 0 568.875 75" enable-background="new 0 0 568.875 75" xml:space="preserve">
  <line fill="none" stroke="#000000" stroke-width="2" stroke-miterlimit="10" x1="568" y1="0" x2="568" y2="60"/>
  <line fill="none" stroke="#000000" stroke-width="2" stroke-miterlimit="10" x1="568" y1="60" x2="3" y2="60"/>
  <g>
    <g>
      <line fill="none" stroke="#000000" stroke-width="2" stroke-miterlimit="10" x1="3" y1="60" x2="3" y2="72.714"/>
      <g>
        <polygon points="-0.391,68.73 3,72.123 6.391,68.73 6.391,71.609 3,75 -0.391,71.609 			"/>
      </g>
    </g>
  </g>
  </svg>
  <div class="hex-container public-key-container">
    <div class="public-key-x-lead hex-left">N/</div>
    <div class="public-key-x hex-right">A</div>
  </div>

  <div class="information step7"><span class="title">7.</span> Utilice la paridad de la coordenada (y) y la coordenada (x) completa para representar la clave pública.</div>
</div>

<div>
  <div class="container">
    <img class="address-hash" src="/assets/imgs/wallet-gen/address-hash.svg" />
    <div class="ripe-hash">
      <div class="ripe160 hex-container hex-padding">N/A</div>
    </div>
    <div class="information step8 information-arrow-left-top"><span class="title">8.</span> Hash la clave pública dos veces. Esto ofusca la clave pública y la abrevia.</div>
  </div>
</div>
</div>

<div class="public-address-container">
  <div class="container">
    <div class="hex-container">
      <div class="hex-left version">00</div>
      <div class="ripe160 hex-middle"></div>
      <div class="hex-right checksum address-checksum"></div>
    </div>
    <div class="information information-arrow-bottom-middle step9"><span class="title">9.</span> Anteponer la versión (el número de versión es diferente al del paso 2)</div>
    <div class="information information-arrow-bottom-middle step10"><span class="title">10.</span> Agregar suma de comprobación (mismo método que en el paso 4)</div>
  </div>
  <div>
    <div class="container">
      <img src="/assets/imgs/wallet-gen/base58-address.svg" />
      <div>
        <div class="hex-container hex-padding public-address">N/A</div>
      </div>
      <div class="information information-arrow-left-top step11"><span class="title">11.</span> Después de otra codificación base58, tenemos nuestra dirección pública :)</div>
    </div>
  </div>
</div>
</div>
