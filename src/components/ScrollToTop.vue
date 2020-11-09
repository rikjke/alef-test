<template>
    <a v-if="scroll" class="scroll-to-top" href="#"><i class="far fa-arrow-alt-circle-up"></i></a>
</template>

<script>
export default {
    methods: {
        getScroll() {
            this.scroll = window.pageYOffset;
        }
    },
    data() {
        return {
            scroll: null,
        }
    },
    created: function () {
        window.addEventListener('scroll', this.getScroll);
    },
    destroyed: function () {
        window.removeEventListener('scroll', this.getScroll);
    }
}
</script>

<style scoped>
    .scroll-to-top {
        position: fixed;
        bottom: 50px;
        right: 40px;
        color: var(--red)
    }
    .scroll-to-top i {
        font-size: 40px;
        transition: .4s ease all;
    }
    .scroll-to-top:hover i {
        transform: scale(1.2)
    }
</style>
    