<template>
    <el-container>
        <el-header>Header</el-header>
        <el-main>Main</el-main>

        <el-footer>
            <el-row>
                <el-col :span="8">
                    Powered by
                    <el-link type="primary">m0nclous</el-link>
                </el-col>

                <el-col :span="8">
                    <el-tag>Seed 018f6062-97c2-4be2-8edf-41beb8e0b275</el-tag>
                </el-col>

                <el-col :span="8">
                    v1.0.0
                </el-col>
            </el-row>
        </el-footer>
    </el-container>
</template>

<script setup>

</script>

<style scoped>
    .el-container {
        margin: auto;
        max-width: 1320px;
        min-height: 700px;
        box-shadow: var(--el-box-shadow-dark);
        border-radius: var(--el-border-radius-base);
        color: var(--el-text-color-primary);
    }

    .el-col:nth-child(2) {
        text-align: center;
    }

    .el-col:nth-child(3) {
        text-align: right;
    }

    .el-header {
        --el-header-padding: 20px;
    }

    .el-footer {
        --el-footer-padding: 20px;
    }
</style>

<style>
    html {
        font-size: 12px;
    }

    body {
        display: flex;
        height: 100vh;
        margin: 0;
    }
</style>