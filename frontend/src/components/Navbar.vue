<template>
    <div class="flex justify-center px-2 py-1 min-h-16 w-full backdrop-blur-md">
        <div class="max-w-[78rem] mx-auto w-full flex justify-between min-h-16">
            <div class="flex overflow-x-auto">
                <NavbarButton href="/" :bold="true"> {{ $t("navbar./") }}</NavbarButton>
                <NavbarButton href="/dependencies"> {{ $t("navbar./dependencies") }}</NavbarButton>
                <NavbarButton href="/mappings"> {{ $t("navbar./mappings") }}</NavbarButton>
            </div>

            <div class="flex">
                <NavbarButton :hover-dim="false">
                    <div class="relative">
                        <div @click="dropdownVisible = !dropdownVisible" class="hover:opacity-70 transition-all">
                            <svg tabindex="0" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" stroke-width="2"
                                 stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round">
                                <path stroke="none" d="M0 0h24v24H0z" fill="none"></path>
                                <path d="M4 5h7"></path>
                                <path d="M7 4c0 4.846 0 7 .5 8"></path>
                                <path d="M10 8.5c0 2.286 -2 4.5 -3.5 4.5s-2.5 -1.135 -2.5 -2c0 -2 1 -3 3 -3s5 .57 5 2.857c0 1.524 -.667 2.571 -2 3.143"></path>
                                <path d="M12 20l4 -9l4 9"></path>
                                <path d="M19.1 18h-6.2"></path>
                            </svg>
                        </div>

                        <transition enter-active-class="transition ease-out duration-100" enter-from-class="transform opacity-0 scale-95"
                                    enter-to-class="transform opacity-100 scale-100" leave-active-class="transition ease-in duration-75"
                                    leave-from-class="transform opacity-100 scale-100" leave-to-class="transform opacity-0 scale-95">
                            <div v-if="dropdownVisible"
                                 class="locale-dropdown absolute right-0 z-10 mt-3 min-w-56 max-w-80 divide-y-2 divide-black/20 origin-top-right rounded-md bg-base-100 dark:bg-base-dark-300 dark:text-base-dark-content shadow-xl ring-4 ring-black ring-opacity-20">
                                <div class="py-1">
                                    <a @click="locale = 'en_US'; $i18n.locale = locale; dropdownVisible = false"
                                       class="cursor-pointer block px-4 py-2 hover:bg-base-300 dark:hover:bg-base-dark-400 transition-colors flex gap-2 items-center">
                                        <p class="flex-1 pr-2">English (US)</p>
                                        <svg xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" preserveAspectRatio="xMidYMid meet"
                                             viewBox="0 0 36 36">
                                            <path fill="#B22334"
                                                  d="M35.445 7C34.752 5.809 33.477 5 32 5H18v2h17.445zM0 25h36v2H0zm18-8h18v2H18zm0-4h18v2H18zM0 21h36v2H0zm4 10h28c1.477 0 2.752-.809 3.445-2H.555c.693 1.191 1.968 2 3.445 2zM18 9h18v2H18z"/>
                                            <path fill="#EEE"
                                                  d="M.068 27.679c.017.093.036.186.059.277c.026.101.058.198.092.296c.089.259.197.509.333.743L.555 29h34.89l.002-.004a4.22 4.22 0 0 0 .332-.741a3.75 3.75 0 0 0 .152-.576c.041-.22.069-.446.069-.679H0c0 .233.028.458.068.679zM0 23h36v2H0zm0-4v2h36v-2H18zm18-4h18v2H18zm0-4h18v2H18zM0 9zm.555-2l-.003.005L.555 7zM.128 8.044c.025-.102.06-.199.092-.297a3.78 3.78 0 0 0-.092.297zM18 9h18c0-.233-.028-.459-.069-.68a3.606 3.606 0 0 0-.153-.576A4.21 4.21 0 0 0 35.445 7H18v2z"/>
                                            <path fill="#3C3B6E" d="M18 5H4a4 4 0 0 0-4 4v10h18V5z"/>
                                            <path fill="#FFF"
                                                  d="m2.001 7.726l.618.449l-.236.725L3 8.452l.618.448l-.236-.725L4 7.726h-.764L3 7l-.235.726zm2 2l.618.449l-.236.725l.617-.448l.618.448l-.236-.725L6 9.726h-.764L5 9l-.235.726zm4 0l.618.449l-.236.725l.617-.448l.618.448l-.236-.725l.618-.449h-.764L9 9l-.235.726zm4 0l.618.449l-.236.725l.617-.448l.618.448l-.236-.725l.618-.449h-.764L13 9l-.235.726zm-8 4l.618.449l-.236.725l.617-.448l.618.448l-.236-.725l.618-.449h-.764L5 13l-.235.726zm4 0l.618.449l-.236.725l.617-.448l.618.448l-.236-.725l.618-.449h-.764L9 13l-.235.726zm4 0l.618.449l-.236.725l.617-.448l.618.448l-.236-.725l.618-.449h-.764L13 13l-.235.726zm-6-6l.618.449l-.236.725L7 8.452l.618.448l-.236-.725L8 7.726h-.764L7 7l-.235.726zm4 0l.618.449l-.236.725l.617-.448l.618.448l-.236-.725l.618-.449h-.764L11 7l-.235.726zm4 0l.618.449l-.236.725l.617-.448l.618.448l-.236-.725l.618-.449h-.764L15 7l-.235.726zm-12 4l.618.449l-.236.725l.617-.448l.618.448l-.236-.725l.618-.449h-.764L3 11l-.235.726zM6.383 12.9L7 12.452l.618.448l-.236-.725l.618-.449h-.764L7 11l-.235.726h-.764l.618.449zm3.618-1.174l.618.449l-.236.725l.617-.448l.618.448l-.236-.725l.618-.449h-.764L11 11l-.235.726zm4 0l.618.449l-.236.725l.617-.448l.618.448l-.236-.725l.618-.449h-.764L15 11l-.235.726zm-12 4l.618.449l-.236.725l.617-.448l.618.448l-.236-.725l.618-.449h-.764L3 15l-.235.726zM6.383 16.9L7 16.452l.618.448l-.236-.725l.618-.449h-.764L7 15l-.235.726h-.764l.618.449zm3.618-1.174l.618.449l-.236.725l.617-.448l.618.448l-.236-.725l.618-.449h-.764L11 15l-.235.726zm4 0l.618.449l-.236.725l.617-.448l.618.448l-.236-.725l.618-.449h-.764L15 15l-.235.726z"/>
                                        </svg>
                                    </a>
                                    <a @click="locale = 'en_GB'; $i18n.locale = locale; dropdownVisible = false"
                                       class="cursor-pointer block px-4 py-2 hover:bg-base-300 dark:hover:bg-base-dark-400 transition-colors flex gap-2 items-center">
                                        <p class="flex-1 pr-2">English (UK)</p>
                                        <svg xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" preserveAspectRatio="xMidYMid meet"
                                             viewBox="0 0 36 36">
                                            <path fill="#00247D"
                                                  d="M0 9.059V13h5.628zM4.664 31H13v-5.837zM23 25.164V31h8.335zM0 23v3.941L5.63 23zM31.337 5H23v5.837zM36 26.942V23h-5.631zM36 13V9.059L30.371 13zM13 5H4.664L13 10.837z"/>
                                            <path fill="#CF1B2B"
                                                  d="m25.14 23l9.712 6.801a3.977 3.977 0 0 0 .99-1.749L28.627 23H25.14zM13 23h-2.141l-9.711 6.8c.521.53 1.189.909 1.938 1.085L13 23.943V23zm10-10h2.141l9.711-6.8a3.988 3.988 0 0 0-1.937-1.085L23 12.057V13zm-12.141 0L1.148 6.2a3.994 3.994 0 0 0-.991 1.749L7.372 13h3.487z"/>
                                            <path fill="#EEE"
                                                  d="M36 21H21v10h2v-5.836L31.335 31H32a3.99 3.99 0 0 0 2.852-1.199L25.14 23h3.487l7.215 5.052c.093-.337.158-.686.158-1.052v-.058L30.369 23H36v-2zM0 21v2h5.63L0 26.941V27c0 1.091.439 2.078 1.148 2.8l9.711-6.8H13v.943l-9.914 6.941c.294.07.598.116.914.116h.664L13 25.163V31h2V21H0zM36 9a3.983 3.983 0 0 0-1.148-2.8L25.141 13H23v-.943l9.915-6.942A4.001 4.001 0 0 0 32 5h-.663L23 10.837V5h-2v10h15v-2h-5.629L36 9.059V9zM13 5v5.837L4.664 5H4a3.985 3.985 0 0 0-2.852 1.2l9.711 6.8H7.372L.157 7.949A3.968 3.968 0 0 0 0 9v.059L5.628 13H0v2h15V5h-2z"/>
                                            <path fill="#CF1B2B" d="M21 15V5h-6v10H0v6h15v10h6V21h15v-6z"/>
                                        </svg>
                                    </a>
                                    <a @click="locale = 'zh_CN'; $i18n.locale = locale; dropdownVisible = false"
                                       class="cursor-pointer block px-4 py-2 hover:bg-base-300 dark:hover:bg-base-dark-400 transition-colors flex gap-2 items-center">
                                        <p class="flex-1 pr-2">中文 (中国)</p>
                                        <svg xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" preserveAspectRatio="xMidYMid meet"
                                             viewBox="0 0 36 36">
                                            <path fill="#DE2910" d="M36 27a4 4 0 0 1-4 4H4a4 4 0 0 1-4-4V9a4 4 0 0 1 4-4h28a4 4 0 0 1 4 4v18z"/>
                                            <path fill="#FFDE02"
                                                  d="m11.136 8.977l.736.356l.589-.566l-.111.81l.72.386l-.804.144l-.144.804l-.386-.72l-.81.111l.566-.589zm4.665 2.941l-.356.735l.566.59l-.809-.112l-.386.721l-.144-.805l-.805-.144l.721-.386l-.112-.809l.59.566zm-.957 3.779l.268.772l.817.017l-.651.493l.237.783l-.671-.467l-.671.467l.236-.783l-.651-.493l.817-.017zm-3.708 3.28l.736.356l.589-.566l-.111.81l.72.386l-.804.144l-.144.804l-.386-.72l-.81.111l.566-.589zM7 10.951l.929 2.671l2.826.058l-2.253 1.708l.819 2.706L7 16.479l-2.321 1.615l.819-2.706l-2.253-1.708l2.826-.058z"/>
                                        </svg>
                                    </a>
                                    <a @click="locale = 'zh_TW'; $i18n.locale = locale; dropdownVisible = false"
                                       class="cursor-pointer block px-4 py-2 hover:bg-base-300 dark:hover:bg-base-dark-400 transition-colors flex gap-2 items-center">
                                        <p class="flex-1 pr-2">中文 (台灣)</p>
                                        <svg xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" preserveAspectRatio="xMidYMid meet"
                                             viewBox="0 0 36 36">
                                            <path fill="#FE0000" d="M32 5H17v13H0v9a4 4 0 0 0 4 4h28a4 4 0 0 0 4-4V9a4 4 0 0 0-4-4z"/>
                                            <path fill="#000095"
                                                  d="M17 5H4a4 4 0 0 0-4 4v9h17V5zm-6.063 4.61l2.035-.548l-1.491 1.487a2.881 2.881 0 0 0-.544-.939zm.251 1.89a2.438 2.438 0 1 1-4.876 0a2.438 2.438 0 0 1 4.876 0zm0-4.222l-.548 2.035a2.871 2.871 0 0 0-.939-.544l1.487-1.491zM8.75 6.625l.542 2.034c-.175-.033-.357-.052-.542-.052s-.367.019-.542.052l.542-2.034zm-.951 2.144a2.881 2.881 0 0 0-.939.544l-.548-2.035l1.487 1.491zm-1.236.841a2.871 2.871 0 0 0-.544.939L4.528 9.062l2.035.548zm-.654 1.348a2.854 2.854 0 0 0 0 1.084L3.875 11.5l2.034-.542zm.11 1.492c.121.348.308.666.544.939l-2.035.548l1.491-1.487zm.293 3.272l.548-2.035c.273.236.591.423.939.544l-1.487 1.491zm2.438.653l-.542-2.034a2.854 2.854 0 0 0 1.084 0l-.542 2.034zm.951-2.144c.348-.121.666-.308.939-.544l.548 2.035l-1.487-1.491zm1.236-.841c.237-.273.423-.591.544-.939l1.491 1.487l-2.035-.548zm.654-1.348a2.854 2.854 0 0 0 0-1.084l2.034.542l-2.034.542z"/>
                                            <path fill="#FFF"
                                                  d="M9.292 8.659L8.75 6.625l-.542 2.034c.175-.033.357-.052.542-.052s.367.019.542.052zM5.857 11.5c0-.185.018-.367.052-.542l-2.034.542l2.034.542a2.93 2.93 0 0 1-.052-.542zm2.351 2.841l.542 2.034l.542-2.034a2.854 2.854 0 0 1-1.084 0zm3.435-2.841c0 .185-.018.367-.052.542l2.034-.542l-2.034-.542c.033.175.052.357.052.542zm-.455-4.222L9.701 8.769c.348.122.666.308.939.544l.548-2.035zm-.251 6.112l2.035.548l-1.491-1.487a2.881 2.881 0 0 1-.544.939zm-4.625 2.332l1.487-1.491a2.889 2.889 0 0 1-.939-.544l-.548 2.035zm.251-6.112l-2.035-.548l1.491 1.487c.121-.348.307-.665.544-.939zm3.138 4.621l1.487 1.491l-.548-2.035a2.881 2.881 0 0 1-.939.544zM6.019 12.45l-1.491 1.487l2.035-.548a2.86 2.86 0 0 1-.544-.939zm1.78-3.681L6.312 7.278l.548 2.035c.274-.237.591-.423.939-.544zm5.173.293l-2.035.548c.237.273.423.591.544.939l1.491-1.487z"/>
                                            <circle cx="8.75" cy="11.5" r="2.438" fill="#FFF"/>
                                        </svg>
                                    </a>
                                </div>
                                <div class="py-1">
                                    <a href="https://github.com/linkie/linkie-web/tree/master/frontend/src/locales"
                                       class="cursor-pointer block px-4 py-2 hover:bg-base-300 dark:hover:bg-base-dark-400 transition-colors flex gap-2 items-center">
                                        <div class="flex-1 pr-2">
                                            <p class="whitespace-nowrap"> {{ $t("navbar.locale.help.0") }} </p>
                                            <p class="whitespace-nowrap"> {{ $t("navbar.locale.help.1") }} </p>
                                        </div>
                                        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" stroke-width="2"
                                             stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round">
                                            <path stroke="none" d="M0 0h24v24H0z" fill="none"></path>
                                            <path d="M11 7h-5a2 2 0 0 0 -2 2v9a2 2 0 0 0 2 2h9a2 2 0 0 0 2 -2v-5"></path>
                                            <line x1="10" y1="14" x2="20" y2="4"></line>
                                            <polyline points="15 4 20 4 20 9"></polyline>
                                        </svg>
                                    </a>
                                </div>
                            </div>
                        </transition>
                    </div>
                </NavbarButton>

                <NavbarButton @click="setDarkMode(!(($event.target as any)?.checked ?? darkMode()))" :key="componentKey">
                    <svg v-if="darkMode()" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"
                         stroke-width="2"
                         stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round">
                        <path stroke="none" d="M0 0h24v24H0z" fill="none"></path>
                        <path d="M7.962 3.949a8.97 8.97 0 0 1 4.038 -.957v.008h.393a7.478 7.478 0 0 0 -2.07 3.308m-.141 3.84c.186 .823 .514 1.626 .989 2.373a7.49 7.49 0 0 0 4.586 3.268m3.893 -.11c.223 -.067 .444 -.144 .663 -.233a9.088 9.088 0 0 1 -.274 .597m-1.695 2.337a9 9 0 0 1 -12.71 -12.749"></path>
                        <path d="M3 3l18 18"></path>
                    </svg>
                    <svg v-else xmlns="http://www.w3.org/2000/svg" class="icon icon-tabler" width="24" height="24" viewBox="0 0 24 24" stroke-width="2"
                         stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round">
                        <path stroke="none" d="M0 0h24v24H0z" fill="none"></path>
                        <path d="M12 3c.132 0 .263 0 .393 0a7.5 7.5 0 0 0 7.92 12.446a9 9 0 1 1 -8.313 -12.454z"></path>
                    </svg>
                </NavbarButton>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import {defineComponent} from "vue"
import NavbarButton from "./NavbarButton.vue"
import {mapWritableState} from "pinia"
import {useI18nStore} from "../app/i18n-store"

export default defineComponent({
    name: "Navbar",
    components: {NavbarButton},
    data() {
        return {
            componentKey: 0,
            dropdownVisible: false,
        }
    },
    computed: {
        ...mapWritableState(useI18nStore, ["locale"]),
    },
    methods: {
        darkMode(): boolean {
            return localStorage.getItem("theme") === "dark"
        },
        setDarkMode(darkMode: boolean) {
            localStorage.setItem("theme", darkMode ? "dark" : "cupcake")
            if (localStorage.getItem("theme") === "dark") {
                document.documentElement.setAttribute("data-theme", "dark")
                document.documentElement.classList.add("dark")
                document.documentElement.style.setProperty("--color-scheme", "dark")
            } else {
                document.documentElement.removeAttribute("data-theme")
                document.documentElement.classList.remove("dark")
                document.documentElement.style.setProperty("--color-scheme", "light")
            }
            this.componentKey++
        },
    },
})
</script>

<style scoped>
</style>