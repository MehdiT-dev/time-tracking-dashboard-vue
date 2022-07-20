<template>
    <article class="category-card">
        <p>
            <img :src="categoryIcon"  alt="">
        </p>
        <div class="category-card-content">
            <div v-show="this.$parent.period === 'weekly'">
                <h3>{{ title }}</h3>
                <p class="current-time">{{ weeklyCurrentTime }}hrs</p>
                <p class="last-time">Last week - {{ weeklyPreviousTime }}hrs</p>
                <p class="options">
                    <Ellipsis/>
                </p>
            </div>
            <div v-show="this.$parent.period === 'monthly'">
                <h3>{{ title }}</h3>
                <p class="current-time">{{ monthlyCurrentTime }}hrs</p>
                <p class="last-time">Last month - {{ monthlyPreviousTime }}hrs</p>
                <p class="options">
                    <Ellipsis/>
                </p>
            </div>
            <div v-show="this.$parent.period === 'daily'">
                <h3>{{ title }}</h3>
                <p class="current-time">{{ dailyCurrentTime }}hrs</p>
                <p class="last-time">Yesterday - {{ dailyPreviousTime }}hrs</p>
                <p class="options">
                    <Ellipsis/>
                </p>
            </div>
        </div>
    </article>
</template>

<script>
import Ellipsis from '@/components/icons/Ellipsis.vue'
export default {
    name: 'CategoryCard',
    components: {
        Ellipsis
    },
    props: ["title", "weeklyCurrentTime", "weeklyPreviousTime", "monthlyCurrentTime", "monthlyPreviousTime", "dailyCurrentTime", "dailyPreviousTime", "categoryIcon"]
}
</script>

<style lang="scss" scoped>
.category-card {
    position: relative;
    height: 160px;
    padding-top: 38px;
    border-radius: 15px;
    overflow: hidden;

    > p {
        position: absolute;
        top: -10px;
        right: 20px;
    }
    .category-card-content {
        position: relative;
        background: $dark-blue;
        border-radius: 15px 15px 0 0;
        width: 100%;
        height: calc(160px - 38px);
        padding: 30px 25px;

        &:hover {
            background: $dark-blue-hover;
            cursor: pointer;
        }

        div {
            display: flex;
            align-items: center ;
            justify-content: space-between;
            flex-wrap: wrap;

            h3 {
                font-weight: 500;
                flex-basis: 100%;
                margin-bottom: 5px; 
            }
            p {
    
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
    
    @include respond (medium) {
        height: 100%;
        width: 40%;
        .category-card-content {
            height: 100%;
            padding-top: 25px 30px;

            div p {
                &.current-time {
                    margin: 15px 0 0;
                    font-size: 2.5em;
                }
                &.last-time {
                    margin: 0 0 7px;
                }
                &.options {
                    top: 25px;
                    right: 30px;
                }
            }
        }
    }

    @include respond (large) {
        height: 100%;
        width: 100%;
        padding-top: 45px;

        .category-card-content {
            height: 100%;
            padding: 30px 30px;

            div p {

                &.current-time {
                    font-size: 3.5em;
                }
                &.last-time {
                    flex-basis: 100%;
                    margin-top: 10px;
                }
            }
        }
    }
}
</style>