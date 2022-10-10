<template>
  <Head>
    <Title>Schuhmacherei Simon Jakob</Title>
    <Link rel="icon" type="image/x-icon" href="./assets/favicon.png"></Link>
  </Head>

  <div class="main">
    <div id="nav">
      <div class="bgnav"></div>
      <NuxtLink class="hometitle" to="/">SCHUHMACHEREI JAKOB</NuxtLink>
      <TheNav />
    </div>
    <NuxtPage />
    <FooterB />
  </div>
</template>

<style>


.layout {
  position: absolute;
  top: 297px;
  left: 0;
  width: 100vw;
  z-index: -1;
  display: none;
}

:root {
  font-size: 1vw;
  font-size: clamp(12px, 1vw, 20px);
}

#__nuxt {
  font-family: Avenir, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #24282d;
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  max-width: 1700px;
  overflow: hidden;
}

p {
  min-height: 1.55rem;
}

a {
  text-decoration: none;
  color: #24282d;
}
.main {
  position: relative;
  width: 89%;
  left: 5.5%;
}
.content {
  padding: 4% 2.5% 4% 2.5%;
  text-align: left;
  font-size: 1.55rem;
  line-height: 1.2;
}

h1 {
  font-size: 3.2rem;
  font-weight: 300;
  margin: 0.8rem 0 1.2rem 0;
  letter-spacing: 0.2rem;
}

h2 {
  font-size: 2rem;
  letter-spacing: 0.02rem;
  font-weight: 300;
  border-style: none none solid none;
  border-width: 1px;
}

.title {
  text-align: left;
  left: 2.5%;
  position: relative;
}

.bgnav {
  position: absolute;
  background-color: white;
  width: 100%;
  height: 100%;
  z-index: -1;
  top: 0;
}

#nav {
  position: relative;
  z-index: 2;
  padding: 5.5% 0 6% 0;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: top;
  flex-wrap: wrap;
  font-size: 2rem;
  letter-spacing: 0.02rem;
  background-color: violet;
}

#nav a {
  text-decoration: none;
  color: #24282d;
}

.hometitle {
  border-style: none !important;
}

#nav a.router-link-exact-active {
  border-style: none none solid none;
  border-width: 1px;
}

@media screen and (max-width: 900px) {
  h1 {
    font-size: 2.7rem;
  }
}
</style>
