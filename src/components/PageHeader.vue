<script setup>
defineProps({
    iconUrl: String,
    siteName: String,

})
const linkList = {
    "a": "#",
    "洛克官网": "https://17roco.qq.com"
}
const linkList1 = [
    { title: '介绍', route: '/about' },
    { title: 'roco', link: '//17roco.qq.com', blank: 1 },
    { title: '反馈', link: '#feedback' }
]
import { ref } from 'vue';
function range(start, stop, step) {
    if (stop === undefined) {
        stop = start;
        start = 0;
    }
    if (step === undefined) {
        step = 1;
    }
    var result = [];
    if (step > 0) {
        for (var i = start; i < stop; i += step) {
            result.push(i);
        }
    } else if (step < 0) {
        for (var i = start; i > stop; i += step) {
            result.push(i);
        }
    }

    return result;
}
const a = ref(false)

</script>

<template>
    <div class="myheader">
        <div class="routebar">
            <div class="back">
                <button @click="$router.back">
                    < </button>
            </div>
            <span class="separator">|</span>
            <span class="routetitle">
                {{ $route.name }}
            </span>
        </div>
        <a class="site" href="/" @click.prevent="$router.push('/')">
            <img class="sitelogo" :src="iconUrl ? iconUrl : 'favicon.ico'" />
            <span class="sitename" v-text="siteName ? siteName : ''"></span>
        </a>

        <nav class="pagenav">

            <ul class="navlist">
                <li v-for="item in linkList1">
                    <a v-if="item.link" :class="{ outlink: item.blank }" :target='item.blank ? "_blank" : ""'
                        :href="item.link">{{ item.title }}</a>
                    <RouterLink v-else :to="item.route">{{ item.title }}</RouterLink>
                </li>
            </ul>

        </nav>
    </div>
</template>

<style scoped>
.routebar {
    align-items: center;
    padding-left: 20px;
    padding-right: 20px;
    margin-right: 5%;
    display: flex;
    max-width: 20%;
    max-height: 100%;
}

.back button {
    transition: 2s;
    background: none;
    border: none;
    cursor: pointer;
    font-size: 1.2em;
    margin-right: 10px;
    font-weight: bold;
}

.routetitle {
    padding: 5px;
    font-weight: bold;
    min-width: 60px;
    max-width: 100px;
}

.separator {
    margin: 0 10px;
}

a.site {
    text-decoration: none;
    height: inherit;

    place-items: inherit;
    display: inherit;
}

a.outlink {
    text-decoration: underline;
}

.myheader {
    height: 100%;
    width: 100%;
    padding: 0 10px;
    display: flex;
    align-items: center;

}

img.sitelogo {
    min-width: 40px;
    min-height: 40px;

    max-height: 80%;
    align-self: center;


}

.sitename {
    font-size: 2rem;
    font-family: '宋体';
    font-weight: bold;
    color: chocolate;
}

nav {
    background-color: transparent;
    width: 80%;
    margin: auto 50px;
    height: 100%;
}

nav ul {
    list-style-type: none;
    margin: 0;
    padding: 0;
    height: 100%;
    display: flex;

    align-items: center;


}

nav ul li {
    display: inline;
    height: auto;
    min-width: 80px;
    margin: 0;
    padding: 0 10px;

    text-align: center;
}

nav ul li a {


    width: 100%;
    font-size: 1.5rem;
    font-family: "宋体";
    color: #9e329eaf;
    text-decoration: none;
    background-color: #fae3d900;
    display: flex;
    align-items: center;
    height: 100%;
    justify-content: center;
    font-weight: bold;

}

nav li:not(:last-child) {
    border-right: 1px solid #caababcc;
}

nav ul li a:hover {
    color: #df37dff1;
    background-color: #ececec77;
}

button.navmenu {
    display: none;
}

@media (max-width: 1024px) {
    .site {
        position: relative;
        width: 100%;
        justify-content: center;
    }

    .pagenav {
        float: right;
        align-items: center;
        justify-content: center;
        height: 100%;
        display: flex;
        overflow-y: visible;
    }


    .navlist {
        display: none;


    }

    button.navmenu {
        display: block;
    }


}
</style>