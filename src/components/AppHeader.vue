<script>
    export default {
        data() {
            return {
                newSearch: ''
            }
        },
    }
</script>

<template>
    <header class="py-3">
        <div class="container">
            <div class="row">
                <div class="col-6 d-flex align-items-center">
                    <div class="card border-0 fs-3 fw-bold">
                        BOOLFIX
                    </div>
                </div>
                <div class="col-6">
                    <div class="card border-0">
                        <div class="input-group">
                            <input class="form-control" placeholder="inserisci il titolo che vuoi ricercare" type="text" v-model="newSearch">
                            <button @click="$emit('searching', newSearch)" class="btn btn-outline-secondary">Cerca</button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </header>
</template>

<style scoped lang="scss">
    
</style>