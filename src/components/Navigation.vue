<template>
  <div id="nav">
        <div id="nav-inner">
            <router-link id="nav-logo" to="/"><img src="@/assets/images/gojani.svg"></router-link>
            <div id="nav-menu">
                <router-link to="/">Home</router-link>
                <router-link to="/imprint">Imprint</router-link>
            </div>
        </div>
    </div>
</template>
<style lang="scss">

#nav {
    width: 100%;
    position: fixed;
    top: 0px;
    transition: 0.3s box-shadow, 0.3s padding-top;
    backdrop-filter: blur(10px);
    background: #FFFFFF44;
}

#nav-inner {
    margin: auto;
    max-width: 1400px;
    width: 100%;
    line-height: 80px;
    height: 90px;
    padding: 5px 20px;
    box-sizing: border-box;
}

#nav-logo  img{
    height: 80px
}

#nav-menu {
    float: right;
}

#nav-menu a,
#nav-menu a:visited,
#nav-menu a:link {
    color: #424242;
    text-decoration: none;
    font-size: 23px;
    margin-left: 10px;
    transition: 0.3s color, 0.3s text-decoration, 0.3s padding-top;
}

#nav-menu a:hover {
    border-bottom: 2px solid #ff285e;
    transition: 0.3s;
}

@media screen and (max-width: 720px) {

    #nav-inner {
        line-height: 60px;
        height: 70px;
        padding: 5px 20px;
        box-sizing: border-box;
    }

    #nav-logo  img{
        height: 60px
    }

    #nav-menu a,
    #nav-menu a:visited,
    #nav-menu a:link {
        font-size: 20px;
    }

}
</style>