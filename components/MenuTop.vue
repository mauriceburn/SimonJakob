<template>
  <div class="mbtn" @click="mbtn = !mbtn" :class="{ expand: mbtn }">
    <div class="lineTop"></div>
    <div class="lineBottom"></div>
  </div>
  <div class="menu" @click="mbtn = false" :class="{ expand: mbtn }">
    <router-link to="/schuhenachmass">SCHUHE NACH MASS</router-link>
    <router-link to="/schuhreparatur">SCHUHREPARATUR</router-link>
    <router-link to="/kontakt">KONTAKT</router-link>
  </div>
</template>

<script>
export default {
  data() {
    return {
      mbtn: false,
    };
  },
};
</script>

<style>
.menu {
  display: flex;
  justify-content: space-between;
  width: clamp(450px, 43%, 43%);
  font-size: 1.35rem;
  margin-top: 0.25%;
}

.mbtn {
  display: none;
  position: relative;
  width: 2rem;
  height: 3rem;
}

.lineTop {
  position: absolute;
  top: 30%;
  border-top: 1px solid #303030;
  transition: all 0.2s ease;
  width: 100%;
}

.lineBottom {
  position: absolute;
  top: 50%;
  border-top: 1px solid #303030;
  transition: all 0.2s ease;
  width: 100%;
}

.expand .lineTop {
  transform: rotate(45deg);
  top: 50%;
}

.expand .lineBottom {
  transform: rotate(-45deg);
  top: 50%;
}

@media screen and (max-width: 900px) {
  .menu {
    flex-direction: column;
    align-items: flex-end;
    width: 100%;
    font-size: 1.5rem;
    gap: 2rem;
    padding-top: calc(2rem + 11.5%);
    position: absolute;
    background-color: white;
    z-index: -2;
    transform: translateY(-100%);
    transition: all 0.2s ease;
  }

  .expand {
    transform: translateY(0);
  }

  .mbtn {
    display: block;
  }

  .text {
    display: block;
  }

  .text > div {
    text-align: left;
    margin-top: 1rem;
  }
  .home {
    flex-direction: column;
    gap: 3rem!important;
  }

  .blocks-gallery-item figure {
  width: 40vw!important;
  height: 40vw!important;
  }
}
</style>
