<script>
    import { store } from '../store.js';

    // components
    import AppContent from './AppContent.vue';
    
    export default {
        components: {
            AppContent,
        },
        data() {
            return {
                store,
            }
        },
    }
</script>

<template>
    <main>
        <section>
            <div class="container-fluid">
                <div class="row">
                    <div class="col">
                        <div class="mycard">
                            <h2 class="m-0 mt-4">ORIGINALI NETFLIX</h2>
                        </div>
                    </div>
                </div>
                <div class="row">
                    <div class="col">
                        <div class="mycard">
                            <ul>
                                <li class="me-3" v-for="(value, index) in store.cards" :key="index">
                                    <AppContent :element="value"/>
                                </li>
                            </ul>
                        </div>
                    </div>
                </div>
            </div>
        </section>
    </main>
</template>

<style scoped lang="scss">
    @use '../styles/partials/variables.scss'as *;

    main {
        flex-grow: 1;
        height: 100%;
        background-color: $bg-brown;
        padding-left: 20px;

        h2 {
            color: $color-white;
        }
        
        ul {
            list-style-type: none;
            padding: 0;
            margin: 0;
            display: flex;
            overflow-x: scroll;
        }
    }
</style>