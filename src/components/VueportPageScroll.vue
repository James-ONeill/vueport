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
        window.addEventListener("scroll", this.recalculateScroll);
        window.addEventListener("resize", this.recalculateScroll);

        this.$once("hook:beforeDestroy", () => {
            window.removeEventListener("scroll", this.recalculateScroll);
            window.removeEventListener("resize", this.recalculateScroll);
        });
    },

    computed: {
        scrollableHeight() {
            return this.scrollHeight - this.clientHeight;
        },

        scrollPcnt() {
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

    render() {
        return this.$scopedSlots.default({
            scrollY: this.scrollY,
            scrollHeight: this.scrollHeight,
            clientHeight: this.clientHeight,
            scrollableHeight: this.scrollableHeight,
            scrollPcnt: this.scrollPcnt,
        });
    }
};
</script>
