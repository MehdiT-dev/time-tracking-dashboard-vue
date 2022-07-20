<template>
    <section class="dashboard">
        <UserCard
            :ref="userCardReference"
            @change-to-daily="period = 'daily'"
            @change-to-weekly="period = 'weekly'"
            @change-to-monthly="period = 'monthly'"
        />
        <CategoryCard v-for="(data, index) in json" :key="data.title"
            :categoryIcon="imgSrc[index]"
            :ref="categoryCardReference"
            :title="data.title"
            :dailyCurrentTime="data.timeframes.daily.current"
            :dailyPreviousTime="data.timeframes.daily.previous"
            :weeklyCurrentTime="data.timeframes.weekly.current"
            :weeklyPreviousTime="data.timeframes.weekly.previous"
            :monthlyCurrentTime="data.timeframes.monthly.current"
            :monthlyPreviousTime="data.timeframes.monthly.previous"
        />
        <Footer/>
    </section>
</template>

<script>
import json from '@/assets/json/data.json'
import CategoryCard from '@/components/CategoryCard.vue'
import UserCard from '@/components/UserCard.vue'
import Footer from '@/components/Footer.vue'
export default {
    name: 'UserDashboard',
    components: {
        CategoryCard,
        UserCard,
        Footer
    },
    data() {
        return {
            json: json,
            period: 'daily',
            userCardReference: 'user',
            categoryCardReference: 'cards',
            categoryCardBg: {
                'work': 'hsl(15, 100%, 70%)',
                'play': 'hsl(195, 74%, 62%)',
                'study': 'hsl(348, 100%, 68%)',
                'exercise': 'hsl(145, 58%, 55%)',
                'social': 'hsl(264, 64%, 52%)',
                'selfCare': 'hsl(43, 84%, 65%)',
                'default': 'hsl(348, 100%, 68%)'
            },
            imgSrc: [],
        }
    },
    methods: {
        updateCards: function() {
            this.$refs.cards.forEach(card => {
                switch (card.$el.children[1].children[0].children[0].innerText.toLowerCase()) {
                    case 'work':
                        card.$el.style.background = this.categoryCardBg.work
                        break;
                    case 'play':
                        card.$el.style.background = this.categoryCardBg.play
                        break;
                    case 'study':
                        card.$el.style.background = this.categoryCardBg.study
                        break;
                    case 'exercise':
                        card.$el.style.background = this.categoryCardBg.exercise
                        break;
                    case 'social':
                        card.$el.style.background = this.categoryCardBg.social
                        break;
                    case 'self care':
                        card.$el.style.background = this.categoryCardBg.selfCare
                        break;
                    default:
                        card.$el.style.background = this.categoryCardBg.default
                }
            });
        },
        loadCategoryIcons: function() {
            json.forEach((data, index) => {
                let categoryTitle = data.title.replace(' ', '-').toLowerCase()
                this.imgSrc[index] = require(`@/assets/images/icon-${categoryTitle}.svg`)
            })
        }
    },
    beforeMount() {
        this.loadCategoryIcons()
    },
    mounted() {
        this.updateCards()
    },
    watch: {
        period: function() {
            let periodLi = Array.from(this.$refs.user.$el.children[1].children[0].children)
            periodLi.forEach(li => {
                if (li.innerText.toLowerCase() === this.period) {
                    li.classList.add('active')
                } else {
                    li.classList.remove('active')
                }
            });
        }
    }
}
</script>

<style lang="scss" scoped>
.dashboard {
    > * {
        margin: 25px auto;

        &:last-child {
            margin: 0 auto;
            padding: 25px;
        }
    }

    @include respond (medium) {
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;

        article {
            flex-basis: calc(50% - 12px);
            margin: 12px 0;

            &:first-child {
                flex-basis: 100%;
            }
            &:last-child {
                flex-basis: 100%;
            }
        }
    }

    @include respond (large) {
        display: grid;
        grid-template-columns: repeat(4, 255px);
        grid-gap: 30px;
        grid-template-rows: repeat(2, 245px);
        margin: calc((100vh - 620px) / 2) auto;
        height: 580px;
        width: 1110px;

        > * {
            &:first-child {
                grid-column: 1/2;
                grid-row: 1/3;
            }
            &:nth-child(0n+2) {
                grid-column: 2/3;
                grid-row: 1/2;
            }
            &:nth-child(0n+3) {
                grid-column: 3/4;
                grid-row: 1/2;
            }
            &:nth-child(0n+4) {
                grid-column: 4/5;
                grid-row: 1/2;
            }
            &:nth-child(0n+5) {
                grid-column: 2/3;
                grid-row: 2/3;
            }
            &:nth-child(0n+6) {
                grid-column: 3/4;
                grid-row: 2/3;
            }
            &:nth-child(0n+7) {
                grid-column: 4/5;
                grid-row: 2/3;
            }
            &:nth-child(0n+8) {
                grid-column: 1/5;
                grid-row: 3;
            }
        }
    }
}
</style>