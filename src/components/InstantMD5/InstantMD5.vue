<template lang="html">
    <div>
        <input
            type="text"
            value=""
            :placeholder="placeholder"
            @input="calculateHash"
        />
        <p>MD5 Hash: {{ this.hash }}</p>
    </div>
</template>

<script>
import hasher from '../../modules/hasher'

export default {
    props: ['placeholder', 'onInputChange'],
    data: function() {
        return {
            hash: ''
        }
    },
    methods: {
        calculateHash(ev) {
            this.hash = hasher(ev.target.value)

            if (window.Interface && typeof window.Interface[this.onInputChange] === 'function') {
                window.Interface[this.onInputChange](ev.target.value)
            }
        }
    }
}
</script>

<style lang="scss" scoped>
    @import "../../styles/colors.scss";

    p {
        color: $default-color;
    }

    input {
        width: 400px;
        padding: 10px;
    }
</style>
