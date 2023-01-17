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
            <div class="container">
                <div class="row">
                    <div class="col">
                        <div class="mycard">
                            <ul>
                                <li v-for="(value, index) in store.cards" :key="index">
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
    ul {
        list-style-type: none;
    }
</style>