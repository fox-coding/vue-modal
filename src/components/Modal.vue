<template>
    <div class="backdrop" @click.self="closeModal">
        <div class="modal" :class="{sale: theme === 'sale'}">
            <slot></slot>
            <div class="actions">
                <slot name="links"></slot>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['theme'],
        methods:{
            closeModal(){
                this.$emit('close')
            }
        }
    }
</script>


<style>
    .backdrop{
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.5);
    }
    .modal{
        background: #fff;
        width: 400px;
        border-radius: 10px;
        height: 500px;
        height: max-content;
        padding: 20px;
        max-height: 80vh;
        max-width: 80vw;
        position: absolute;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        box-shadow: 0 0 15px -5px black;
        margin: auto;
    }
    .modal.sale{
        background: crimson;
        color: #fff;
    }
    .modal h2{
        font-size: 1.5em;
    }
    .modal .actions a{
        margin: 0 10px;
        font-size: 12px;
    }

</style>