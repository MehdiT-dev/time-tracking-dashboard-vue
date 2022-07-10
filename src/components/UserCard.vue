<template>
    <article class="user-card">
        <div class="user-card-content">
            <p class="user-picture">
                <img src="@/../images/image-jeremy.png" alt="">
            </p>
            <div class="user-info">
                <p>Report for</p>
                <h2>Jeremy Robson</h2>
            </div>
        </div>
        <div class="period-display">
            <ul>
                <li><a href="">Daily</a></li>
                <li><a href="">Weekly</a></li>
                <li><a href="">Monthly</a></li>
            </ul>
        </div>
    </article>
</template>

<script>
export default {
    name: 'CategoryCard',
}
</script>

<style lang="scss" scoped>
.user-card {
    background-color: $dark-blue;
    border-radius: 15px;
    overflow: hidden;
    height: 200px;
    color: $white;

    .user-card-content {
        display: flex;
        align-items: center;
        justify-content: space-between;
        background: $blue;
        border-radius: 15px;
        width: 100%;
        padding: 30px;

        p {
            &.user-picture {
                width: 70px;
                height: 70px;

                img {
                    width: 100%;
                    border: 3px solid $white;
                    border-radius: 50%;
                }
            }
        }
        .user-info {
            p {
                color: $pale-blue;
            }
            h2 {
                font-weight: 300;
            }
        }
    }
    .period-display {
        padding: 30px 0;

        ul {
            display: flex;
            justify-content: space-between;
            align-items: center;

            li {
                flex-basis: 33%;
                text-align: center;
                display: inline-block;
                list-style-type: none;

                a {
                    color: $white;
                    text-decoration: none;
                }
            }
        }
    }
}
</style>