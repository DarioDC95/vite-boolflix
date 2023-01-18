<script>
    export default {
        emits: [
            'searching',
        ],
        data() {
            return {
                newSearch: ''
            }
        },
        methods: {
            clickSearch() {
                if(this.newSearch != '' && this.newSearch.replace(/\s/g, '').length != 0) {
                    this.$emit('searching', this.newSearch)
                }
                else {
                    this.newSearch = ''
                }
            }
        }
    }
</script>

<template>
    <header>
        <div class="container-fluid">
            <div class="row justify-content-between">
                <div class="col-6 d-flex align-items-center">
                    <div class="mycard fs-3 fw-bold">
                        <img src="../assets/Netflix_Logo_PMS.png" alt="Logo Netflix">
                    </div>
                </div>
                <div class="col-6 d-flex align-items-center">
                    <div class="card flex-row justify-content-end w-100 border-0">
                        <div>
                            <button @click="clickSearch()" class="buttonSearch"><font-awesome-icon icon="fa-solid fa-magnifying-glass" /></button>
                            <input @keyup.enter="clickSearch()" class="input-search" placeholder="inserisci il titolo che vuoi ricercare" type="text" v-model="newSearch">
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </header>
</template>

<style scoped lang="scss">
    @use '../styles/partials/variables.scss'as *;

    header {
        background-color: $bg-black;

        img {
            width: 200px;
        }

        .card {
            background-color: transparent;

            .buttonSearch {
                margin-right: 0.50rem;
                padding: 4px 10px;
                border-radius: 8px;
                background-color: transparent;
                color: $color-white;
                font-weight: 900;
                font-size: 18px;
                border: 3px solid black;

                &:hover {
                    box-shadow: 0px 0px 3px 5px lightblue;;
                }

                &:active {
                    background-color: $bg-white;
                    color: black;
                }
            }

            .input-search{
                --webkit-appearance-: none;
                border: none;
                border-radius: 5px;
                background-color: white;
                padding: 7px 10px;
                width: 300px;

                &:focus-visible {
                    outline: none;
                    box-shadow: 0px 0px 3px 5px lightblue;
                }
            }
        }
    }
    
</style>