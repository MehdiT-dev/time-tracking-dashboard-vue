<template>
    <footer>
        <p>Challenge by <a href="https://www.frontendmentor.io?ref=challenge" target="_blank">Frontend Mentor</a>.</p>
        <p>Coded by <a href="https://github.com/MehdiT-dev" target="_blank">Mehdi Tadjer</a>.</p>
    </footer>
</template>

<script>
export default {
    name: 'Footer'
}
</script>

<style lang="scss" scoped>
    footer {
        padding: 10px;
        text-align: center;

        p {
            color: $blue;
        }
        a {
            text-decoration: none;
            padding: 6px 3px;
            color: $white;

            &:hover {
                background: $blue;
            }
        }
    }
</style>