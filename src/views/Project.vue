<template>
    <div>
        <div class="contents">
            <h1>{{current.name}}</h1>
            <a class="project-button" v-for="(link, key) in current.buttons" :key="key" target="_blank" :href="link">{{key}}</a>
            <div id="screenshots">
                <img v-for="key in current.screenshots" :key="key" :src="key">
            </div>
            <div id="readme" v-html="current.readme"></div>
        </div>
    </div>
</template>
<script>
import { Cajax } from "cajaxjs";
export default {
    data: ()=>({
        "projects": {
            "pastefy": {
                "name": "Pastefy",
                "github": "interaapps/pastefy",
                "readme": "There is no README file",
                "buttons": {
                    "Source-Code": "https://github.com/interaapps/pastefy",
                    "Visit the Website": "https://pastefy.ga"
                },
                "screenshots": [
                    require("@/assets/images/references/pastefy.png"),
                    require("@/assets/images/screenshots/pastefy/screenshot-1.png")
                ]
            },
            "punyshort": {
                "name": "Punyshort",
                "github": "interaapps/punyshort",
                "readme": "There is no README file",
                "buttons": {
                    "Source-Code": "https://github.com/interaapps/punyshort",
                    "Visit the Website": "https://punyshort.ga"
                },
                "screenshots": [
                    require("@/assets/images/references/punyshort.png")
                ]
            },
            "quotysco": {
                "name": "Quotysco",
                "github": "interaapps/quotysco",
                "readme": "There is no README file",
                "buttons": {
                    "Source-Code": "https://github.com/interaapps/quotysco",
                    "Visit the Website": "https://quotysco.eu"
                },
                "screenshots": [
                    require("@/assets/images/screenshots/quotysco/screenshot.png"),
                    require("@/assets/images/screenshots/quotysco/screenshot-2.png")
                ]
            },
            "passwords": {
                "name": "InteraApps Passwords",
                "github": "interaapps/passwords-frontend",
                "readme": "There is no README file",
                "buttons": {
                    "Source-Code": "https://github.com/interaapps/passwords-frontend",
                    "Visit the Website": "https://passwords.interaapps.de/"
                },
                "screenshots": [
                    require("@/assets/images/screenshots/passwords/screenshot.png"),
                    require("@/assets/images/screenshots/passwords/screenshot-2.png")
                ]
            }
        },
        current: null
    }),
    created(){
        this.$data.current = this.$data.projects[this.$route.params.name];
            if (this.current !== null) {
            Cajax.get("https://api.github.com/repos/"+this.current.github).then((res)=>{
                const parsed = JSON.parse(res.responseText);
                console.log(parsed);

                Cajax.get("https://api.github.com/repos/"+this.current.github+"/readme").then((readme)=>{
                    const MarkdownIt = require("markdown-it");
                    let md = new MarkdownIt("default", {
                        html: true
                    });
                    md.html = true;
                    this.$data.current.readme = md.render(atob(JSON.parse(readme.responseText).content));
                }).send();
            }).send();
        }
    }
}
</script>
<style lang="scss">

    .project-button {
        margin-right: 10px;;
    }

    #screenshots {
        margin: auto;
        text-align: center;
        margin-top: 60px;
        margin-bottom: 100px;
        width: 100%;
    
        img {
            max-width: 100%;
            border-radius: 10px;
            width: 630px;
            margin: 3px 20px;
            box-shadow: rgba(0, 0, 0, 0.09) 0px 0px 14px 1px;
        }
    }

    #readme {

        pre {
            overflow: auto;
        }

        p {
            font-size: 20px;
        }

        h1 {
            font-size: 30px;
        }

        h1, h2 {
            border-bottom: 2px #00000033 solid;
            padding-bottom: 10px;
            margin-bottom: 14px;
            margin-top: 20px;
        }
    }

    @media screen and (max-width: 720px) {
        #screenshots {
            img {
                width: 90%;
                box-shadow: rgba(0, 0, 0, 0.3) 0px 2px 4px 1px;
                display: block;
            }
        }
    }
</style>