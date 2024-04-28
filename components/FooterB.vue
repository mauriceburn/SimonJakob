<template>
  <div class="footer">
    <div class="line"></div>
    <div class="text">
      <div class="leftText">
        Schumacherei Jakob <br />
        Breitenrainplatz 42 <br />3014 Bern
      </div>
      <div class="middleText">
        031 332 66 24 <br /><a href="mailto:mail@schuhmacherei-jakob.ch"
          >mail@schuhmacherei-jakob.ch</a
        >
      </div>
      <div class="rightText">
        <NuxtLink to="/datenschutz">Datenschutz <br /></NuxtLink>
        <NuxtLink to="/impressum">Impressum</NuxtLink>
      </div>
    </div>
  </div>
</template>

<script></script>

<style>
.footer {
  margin-top: 8%;
}

.line {
  border-style: solid none none none;
  border-width: 1px;
  width: 100%;
}

.text {
  padding: 3.6% 0 4% 0;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: flex-end;
  font-size: 1.3rem;
}

.leftText {
  text-align: left;
  width: 33%;
}

.middleText {
  text-align: center;
  width: 33%;
  white-space: nowrap;
}

.rightText {
  text-align: right;
  width: 33%;
  z-index: 3;
}

@media screen and (max-width: 900px) {
  .text {
    display: block;
  }
  .text > div {
    text-align: center !important;
    width: 100%;
  }
}
</style>
