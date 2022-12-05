<template>
    <el-container>
        <el-header>
            <el-steps :active="null" finish-status="success" align-center>
                <el-step title="Категории" description="Импорт категорий" />
                <el-step title="Изображения" description="Импорт изображений" />
                <el-step title="Товары" description="Импорт товаров" />
                <el-step title="Предложения" description="Импорт вариаций" />
                <el-step title="Оптимизация" description="Оптимизация БД" />
            </el-steps>
        </el-header>

        <el-main>
            <el-row>
                <el-col></el-col>

                <el-col>
                    <el-progress type="circle" :percentage="0">
                        <el-button type="success" size="large" circle>
                            <el-icon size="28">
                                <SwitchButton />
                            </el-icon>
                        </el-button>
                    </el-progress>
                </el-col>

                <el-col></el-col>
            </el-row>
        </el-main>

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
    import { SwitchButton } from '@element-plus/icons-vue';

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
        --el-header-height: 100%;
    }

    .el-footer {
        --el-footer-padding: 20px;
    }

    .el-main {
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .el-button--large {
        --el-button-size: 48px;
    }
</style>

<style>
    html {
        font-size: 12px;
        font-family: 'Roboto', sans-serif;
    }

    body {
        display: flex;
        height: 100vh;
        margin: 0;
    }
</style>