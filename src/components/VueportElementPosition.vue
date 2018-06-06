<script>
export default {
    data() {
        return {
            boundingClientRect: null,
            shown: false,
        }
    },

    mounted() {
        this.boundingClientRect = this.$el.getBoundingClientRect();

        window.addEventListener('scroll', this.updateBoundingRect);
        window.addEventListener('resize', this.updateBoundingRect);

        this.$once("hook:beforeDestroy", () => {
            window.removeEventListener("scroll", this.updateBoundingRect);
            window.removeEventListener("resize", this.updateBoundingRect);
        });
    },

    watch: {
        fullyVisible(value) {
            if (this.shown || ! value) return;

            this.shown = true;
        },
    },

    computed: {
        visible() {
            if (! this.boundingClientRect) return false;

            return
                this.boundingClientRect.bottom > 0 &&
                this.boundingClientRect.top < window.innerHeight;
        },

        fullyVisible() {
            if (! this.boundingClientRect) return false;

            return
                this.boundingClientRect.top > 0 &&
                this.boundingClientRect.bottom < window.innerHeight;
        },
    },

    methods: {
        updateBoundingRect() {
            if (this.scrolling) return;

            this.scrolling = true;

            requestAnimationFrame(() => {
                this.boundingClientRect = this.$el.getBoundingClientRect();

                this.scrolling = false;
            });
        },
    },

    render() {
        return this.$scopedSlots.default({
            boundingClientRect: this.boundingClientRect,
            visible: this.visible,
            fullyVisible: this.fullyVisible,
            shown: this.shown
        });
    }
}
</script>

