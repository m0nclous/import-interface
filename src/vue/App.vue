<template>
    <el-container>
        <el-header>
            <el-steps :active="2" finish-status="success" align-center>
                <el-step title="Категории" description="Импорт категорий" />
                <el-step title="Изображения" description="Импорт изображений" />
                <el-step title="Товары" description="Импорт товаров" />
                <el-step title="Предложения" description="Импорт вариаций" />
                <el-step title="Оптимизация" description="Оптимизация БД" />
            </el-steps>
        </el-header>

        <el-main>
            <el-row>
                <el-col :span="6" :offset="4">
                    <el-row>
                        <el-col>
                            <el-alert title="Импорт категорий" type="success" :closable="false">
                                <div>79 / 79 обработано</div>
                                <el-progress :percentage="100" :show-text="false" />
                            </el-alert>
                        </el-col>

                        <el-col>
                            <el-alert title="Импорт изображений" type="success" :closable="false">
                                <div>300 / 300 обработано</div>
                                <el-progress :percentage="100" :show-text="false" />
                            </el-alert>
                        </el-col>
                    </el-row>
                </el-col>

                <el-col :span="5">
                    <el-progress type="circle" :percentage="0">
                        <el-button type="danger" size="large" circle>
                            <el-icon size="28">
                                <SwitchButton />
                            </el-icon>
                        </el-button>
                    </el-progress>
                </el-col>

                <el-col :span="6">
                    <el-row>
                        <el-col>
                            <el-alert title="Импорт товаров" type="process" :closable="false">
                                <div>25 000 / 50 000 позиций</div>
                                <el-progress :percentage="50" :show-text="false" />
                            </el-alert>
                        </el-col>

                        <el-col>
                            <el-alert title="Импорт вариаций" type="info" :closable="false">
                                <div>0 / 50 000 позиций</div>
                                <el-progress :percentage="0" :show-text="false" />
                            </el-alert>
                        </el-col>
                    </el-row>
                </el-col>
            </el-row>

            <el-row style="text-align: center; margin-top: 40px;">
                <el-col>Последняя синхронизация 24.11.2022 20:48</el-col>
                <el-col><b>import0_1.xml</b> обновлён 05.12.2022 16:25</el-col>
                <el-col><b>offers0_1.xml</b> обновлён 05.12.2022 16:25</el-col>
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

    .el-footer .el-col:nth-child(2) {
        text-align: center;
    }

    .el-footer .el-col:nth-child(3) {
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
        flex-direction: column;
    }

    .el-main > .el-row {
        width: 100%;
    }

    .el-main .el-row {
        row-gap: 20px;
    }

    .el-main > .el-row > .el-col:nth-child(2) {
        text-align: center;
        align-self: center;
    }

    .el-alert:deep(.el-alert__content) {
        display: flex;
        flex-direction: column;
        width: 100%;
    }

    .el-alert .el-progress {
        padding: 7px 0;
    }

    .el-alert--process {
        --el-alert-bg-color: var(--el-color-primary-light-9);
        background-color: var(--el-alert-bg-color);
        color: var(--el-color-info);
    }

    .el-alert--success:deep(.el-progress-bar__inner) {
        background-color: var(--el-color-success);
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