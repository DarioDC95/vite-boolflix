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
                    <div v-if="store.cards.length !== 0" class="col">
                        <div class="mycard">
                            <ul>
                                <li class="me-3" v-for="(value, index) in store.cards" :key="index">
                                    <AppContent :element="value"/>
                                </li>
                            </ul>
                        </div>
                    </div>
                    <div v-if="store.cards.length === 0 && store.loading == false" class="col">
                        <div class="card mt-4 align-items-center justify-content-center">
                            <h1>NESSUN RISULTATO TROVATO</h1>
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
        padding: 0 20px;

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

        .card {
            height: 500px;
        }
    }
</style>