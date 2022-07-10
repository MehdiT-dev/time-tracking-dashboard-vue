<template>
    <article class="category-card">
        <div class="category-card-content">
            <h3>Work</h3>
            <p class="current-time">32hrs</p>
            <p class="last-time">Last Week - 36hrs</p>
            <p class="options">
                <img src="@/../images/icon-ellipsis.svg" alt="">
            </p>
        </div>
    </article>
</template>

<script>
export default {
    name: 'CategoryCard',
}
</script>

<style lang="scss" scoped>
.category-card {
    padding-top: 40px;
    background-color: $light-red;
    border-radius: 15px;
    overflow: hidden;

    .category-card-content {
        position: relative;
        display: flex;
        align-items: center ;
        justify-content: space-between;
        flex-wrap: wrap;
        background: $dark-blue;
        border-radius: 15px 15px 0 0;
        width: 100%;
        height: 120px;
        padding: 30px 25px;

        h3 {
            font-weight: 500;
            flex-basis: 100%;
            margin-bottom: 5px; 
        }
        p {
            // line-height: 2em;

            &.current-time {
                font-size: 2em;
            }
            &.last-time {
                align-self:flex-end;
                margin-bottom: 10px;
                color: $pale-blue;
            }
            &.options {
                position: absolute;
                top: 30px;
                right: 25px;
                cursor: pointer;

            }
        }
    }
}
</style>