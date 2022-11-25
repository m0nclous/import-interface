<template>
    <el-container>
        <el-header>Header</el-header>
        <el-main>Main</el-main>
        <el-footer>Footer</el-footer>
    </el-container>
</template>

<script setup>

</script>

<style scoped>
    .el-container {
        margin: auto;
        max-width: 1320px;
        box-shadow: var(--el-box-shadow-dark);
        border-radius: var(--el-border-radius-base);
    }

    .el-header {
        --el-header-padding: 20px;
    }

    .el-footer {
        --el-footer-padding: 20px;
    }
</style>

<style>
    body {
        display: flex;
        height: 100vh;
        margin: 0;
    }
</style>