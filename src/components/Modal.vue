<template>
    <div class="backdrop" @click.self="closeModal">
        <div class="modal" :class="{ sale: theme === 'sale' }">
            <h1>{{ header }}</h1>
            <p>{{ text }}</p>
        </div>
    </div>
</template>

<script>
export default {
    // prop tas pats kas ir data ten grazina reiksmes, kaip ir cia
    // uzregistravome mes cia dabar
    props: ['header', 'text', 'theme'],
    methods: {
        closeModal() {
            // $emit kaip koks addeventlistener tik jis buna custom
            this.$emit('close')
        }
    }

    // data() {
    //     return {
    //         title: 'Vue new',
    //     }
    // },
}
</script>

// scoped reiskia kad CSS butu taikomas tik sitam failui, ne kitiems
<style scoped>

    .modal {
        width: 400px;
        padding: 20px;
        margin: 100px auto;
        background-color: white;
        border-radius: 10px;
    }

    .backdrop {
        top: 0;
        position: fixed;
        background: rgba(0, 0, 0, 0.5);
        width: 100%;
        height: 100%;
    }

    h1 {
        color: #03cfb4;
        border: none;
        padding: 0;
    }

    .modal.sale {
        background: crimson;
        color: white;
    }
    .modal.sale h1 {
        color: white;
    }

</style>