<template>
    <div class="scroll-progress-container">
        <div class="scroll-progress" :style="{ width: `${scrollPercentage}%` }"/>
    </div>
</template>

<script>
export default {
    data() {
        return {
            scrollY: window.scrollY,
            scrollHeight: document.documentElement.scrollHeight,
            clientHeight: document.documentElement.clientHeight,
        };
    },

    created() {
        const scrollListener = window.addEventListener("scroll", this.recalculateScroll);
        const resizeListener = window.addEventListener("resize", this.recalculateScroll);
    },

    computed: {
        scrollableHeight() {
            return this.scrollHeight - this.clientHeight;
        },

        scrollPercentage() {
            return (this.scrollY / this.scrollableHeight) * 100;
        }
    },

    methods: {
        recalculateScroll() {
            if (this.scrolling) return;

            this.scrolling = true;

            requestAnimationFrame(() => {
                this.scrollY = window.scrollY;
                this.scrollHeight = document.documentElement.scrollHeight;
                this.clientHeight = document.documentElement.clientHeight;

                this.scrolling = false;
            });
        }
    },
}
</script>

<style>
.scroll-progress-container {
    bottom: 0;
    height: 6px;
    position: fixed;
    left: 0;
    width: 100%;
}

.scroll-progress {
    background-color: green;
    height: 100%;
}
</style>


