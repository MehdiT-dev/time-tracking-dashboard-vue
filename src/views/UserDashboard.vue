<template>
    <section class="dashboard">
        <UserCard/>
        <CategoryCard/>
        <CategoryCard/>
        <CategoryCard/>
        <CategoryCard/>
        <CategoryCard/>
        <CategoryCard/>
    </section>
</template>

<script>
import CategoryCard from '@/components/CategoryCard.vue'
import UserCard from '@/components/UserCard.vue'
export default {
    name: 'UserDashboard',
    components: {
        CategoryCard,
        UserCard
    }
}
</script>

<style lang="scss" scoped>
.dashboard {
    > * {
        margin: 20px auto;
    }
}
</style>