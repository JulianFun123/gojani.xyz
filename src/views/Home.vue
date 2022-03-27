<template>
  <div>
    <div class="contents">
        <h1 id="title">Julian Gojani</h1>
        <p style="text-align: center; margin-bottom: 240px">
        </p>

        <h1 class="page-titles">What I've done</h1>

        <div class="references">
            <router-link id="pastefy" to="/project/pastefy">
                <h3>Pastefy.ga</h3>
                <h5>A code paster</h5>
            </router-link>

            <router-link id="punyshort" to="/project/punyshort">
                <h3>Punyshort.ga</h3>
                <h5>A link-shortener</h5>
            </router-link>
        </div>
        <div class="references">
            <router-link id="quotysco" to="/project/quotysco">
                <h3>Quotysco.eu</h3>
                <h5>A blogging platform</h5>
            </router-link>

            <router-link id="passwords" to="/project/passwords">
                <h3>InteraApps Passwords</h3>
                <h5>A password manager</h5>
            </router-link>
        </div>

        <div class="references">
            <a id="interaapps" href="https://interaapps.de">
                <h3>interaapps.de</h3>
                <h5>The most of what I am doing is here</h5>
            </a>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Home',
  components: {
  }
}
</script>

<style lang="scss">
    #title {
        font-weight: 300;
        text-align: center;
        font-size: 50px;
        padding-top: 100px;
        margin-bottom: 50px;
    }

    .references {
        display: flex;
        transition: 0.3;

        #punyshort {
          background-image: linear-gradient(#00000022, #00000022), url(../assets/images/references/punyshort.png); color: #FFFFFF
        }

        #pastefy {
          background-image: url(../assets/images/references/pastefy.png); color: #FFFFFF
        }

        #quotysco {
          background-image: url( ../assets/images/screenshots/quotysco/screenshot.png); color: #181818
        }

        #passwords {
          background-image: linear-gradient(#00000008, #00000008), url( ../assets/images/screenshots/passwords/screenshot.png); color: #181818
        }

        #interaapps {
          background-image: url(../assets/images/references/interaapps.svg);
          color: #434343
        }
    }

    .references a {
        box-shadow: rgba(0, 0, 0, 0.1) 0px 0px 8px 0px;
        background-repeat: no-repeat;
        background-position: center;
        background-size: cover;
        width: calc(100% - 10px);
        margin: 5px;
        text-align: center;
        border-radius: 10px;
        padding: 40px 0px;
        display: block;
        margin-bottom: 20px;
        transition: 0.3s;
    }

    .references a:hover {
        box-shadow: rgba(0, 0, 0, 0.2) 0px 2px 5px 0px;
    }


    .references a:hover {
        text-decoration: none !important;
    }

    .references a h3 {
        margin-top: 50px;
    }

    .references a h5 {
        margin-top: 20px;
        margin-bottom: 50px;
        font-size: 20px;
    }

    @media screen and (max-width: 720px) {
        .references {
            display: block;
        }
        
        .references a {
            width: 100%;
            margin: 0px;
            margin-bottom: 40px;
        }
    }
</style>