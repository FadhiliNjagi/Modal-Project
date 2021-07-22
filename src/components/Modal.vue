<template>
    <div class="backdrop" @click.self="closeModal">
        <div class="modal" :class="{ red: theme === 'sale' }">
            <slot>Default content</slot>
            <div class="actions">
                <slot name="links"><a href="#">Links go here</a></slot>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['theme'],
        methods: {
            closeModal() {
                this.$emit('close')
            }
        },
    }
</script>

<style>
    .modal {
        width: 400px;
        padding: 20px;
        margin: 100px auto;
        background: white;
        border-radius: 10px;
    }
    .backdrop {
        top: 0;
        position: fixed;
        background: rgba(0,0,0,0.5);
        width: 100%;
        height: 100%;
    }
    .modal.red {
        background-color: red;
        color: white;
    }
    .modal .actions a {
        color: #333;
        padding: 8px;
        border: 1px solid #eee;
        border-radius: 4px;
        text-decoration: none;
        margin: 10px;
    }
    .modal.red a {
        color: white;
    }
</style>