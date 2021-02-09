<template>
    <div class="backdrop" @click.self="closeModal">
        <div class="modal" :class="{ sale: theme === 'sale' }">
            <!-- <h1>{{ header }}</h1>
            <p>{{ text }}</p> -->
            <!-- galima irasyti i slots ir defaul kazka jei nieko nera paduoto -->
            <slot></slot>
            <div class="actions">
                <!-- slots reikalingi kai nori tam tikra content parodyti tam tikroje area -->
            <slot name="links"></slot>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    // prop tas pats kas ir data ten grazina reiksmes, kaip ir cia
    // uzregistravome mes cia dabar
    // props baigesi, ji naudojam permeti visokia data, array, bool, string, integer ir pan.
    // props: ['header', 'text', 'theme'],
    props: ['theme'],
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
<style>

    .modal {
        width: 400px;
        padding: 20px;
        margin: 100px auto;
        background-color: white;
        border-radius: 10px;
    }

    .modal p {
        font-style: normal;
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

    .modal .actions {
        text-align: center;
        margin: 30px 0 10px 0;
    }

    .modal .actions a {
        color: #333;
        padding: 8px;
        border: 1px solid #eee;
        border-radius: 4px;
        text-decoration: none;
        margin: 10px;
    }

    .modal.sale .actions {
        color: white;
    }

    .modal.sale .actions a {
        color: white;
    }

</style>