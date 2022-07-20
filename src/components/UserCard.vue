<template>
    <article class="user-card">
        <div class="user-card-content">
            <p class="user-picture">
                <img src="../assets/images/image-jeremy.png" alt="">
            </p>
            <div class="user-info">
                <p>Report for</p>
                <h2>Jeremy Robson</h2>
            </div>
        </div>
        <div class="period-display">
            <ul>
                <li @click="$emit('changeToDaily', 'period')" class="active">Daily</li>
                <li @click="$emit('changeToWeekly', 'period')">Weekly</li>
                <li @click="$emit('changeToMonthly', 'period')">Monthly</li>
            </ul>
        </div>
    </article>
</template>

<script>
export default {
    name: 'CategoryCard',
    props: ['period'],
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
        background: $blue;
        border-radius: 15px;
        height: 130px;
        width: 100%;
        padding: 30px;

        p {
            &.user-picture {
                width: 70px;
                height: 70px;
                margin-right: 15px;

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
        height: 70px;

        ul {
            display: flex;
            justify-content: space-between;
            align-items: center;
            height: 100%;

            li {
                flex-basis: 33%;
                text-align: center;
                display: inline-block;
                list-style-type: none;
                cursor: pointer;
                color: $desaturated-blue;
                font-weight: 400;
                font-size: 1.1em;

                &.active,
                &:hover {
                    color: $white;
                }
            }
        }
    }

    @include respond (medium) {
        height: 210px;

            .user-card-content {
                p.user-picture {
                    height: 80px;
                    width: 80px;
                }
                .user-info {
                    h2 {
                        font-size: 2.5em;
                    }
                }
            }
    }

    @include respond (large) {
        height: 100%;

        .user-card-content {
            height: 350px;
            flex-direction: column;
            align-items: flex-start;
            justify-content: space-between;
            padding: 35px 30px 75px;

            p.user-picture {
                height: 85px;
                width: 85px;
            }
        }
        .period-display {
            height: calc(100% - 350px);
            padding: 30px 30px 10px;

            ul {
                flex-direction: column;
                align-items: flex-start;
                justify-content: space-around;
                height: 100%;

                li {
                    flex-basis: 100%;
                }
            }
        }
    }
}
</style>