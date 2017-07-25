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
    props: ['placeholder'],
    data: function() {
        return {
            hash: ''
        }
    },
    methods: {
        calculateHash(ev) {
            this.hash = hasher(ev.target.value)
        }
    }
}
</script>

<style lang="scss" scoped>
    @import "../../styles/main.scss";

    p {
        color: $default-color;
    }

    input {
        width: 400px;
        padding: 10px;
    }
</style>
