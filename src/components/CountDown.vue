<template>
    <div class="countdown">
        <slot>
            {{seconds}}
        </slot>
    </div>
</template>

<script>
export default {
    props: ['time', 'autoStart'],
    data() {
        return {
            seconds: null,
        }
    },
    created() {
        this.init()
        if (this.autoStart !== false)
            this.start()

        // Events
        this.$on('stop', this.stop)
        this.$on('start', this.start)
        this.$on('restart', this.restart)
    },
    watch: {
        seconds() {
            this.countDownProgress()
            if (this.seconds <= 0)
                this.countDownFinished()
        }
    },
    methods: {
        init() {
            this.seconds = this.time
        },
        restart() {
            this.stop()
            this.init()
            this.start()
        },
        start() {
            this.interval = setInterval(
                () => this.seconds--                
            , 1000)
        },
        stop() {
            clearInterval(this.interval)
        },
        countDownFinished() {
            this.stop()
            this.$emit('onFinish')
        },
        countDownProgress() {
            this.$emit('onProgress', this.seconds)
        }
    },
}
</script>

<style lang="scss">
</style>
