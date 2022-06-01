<template>
    <header>
        <h1>{{ title }}</h1>
    </header>
</template>

<script>
export default {
    name: 'HeaderPage',
    props: {
        title: String
    }
}

</script>

<style scoped>
h1 {
    padding-bottom: 85px;
}
</style>
