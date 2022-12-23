<template>
    <el-container>
        <el-header>
            <el-steps :active="importInfo.step" finish-status="success" align-center>
                <el-step v-for="step in steps" :title="step.title" :description="step.description" />
            </el-steps>
        </el-header>

        <el-main>
            <el-row>
                <el-col :span="6" :offset="4">
                    <el-row>
                        <el-col>
                            <el-alert title="Импорт категорий" :type="importInfo.categories.processed === importInfo.categories.total ? 'success' : importInfo.categories.processing ? 'warning' : 'info'" :closable="false">
                                <div>{{ importInfo.categories.processed }} / {{ importInfo.categories.total }} обработано</div>
                                <el-progress :percentage="importInfo.categories.processed / importInfo.categories.total * 100" :show-text="false" />
                            </el-alert>
                        </el-col>

                        <el-col>
                            <el-alert title="Импорт изображений" :type="importInfo.images.processed === importInfo.images.total ? 'success' : importInfo.images.processing ? 'warning' : 'info'" :closable="false">
                                <div>{{ importInfo.images.processed }} / {{ importInfo.images.total }} обработано</div>
                                <el-progress :percentage="importInfo.images.processed / importInfo.images.total * 100" :show-text="false" />
                            </el-alert>
                        </el-col>
                    </el-row>
                </el-col>

                <el-col :span="5">
                    <el-progress type="circle" :percentage="0">
                        <el-button @click="importInProcessing ? importStop() : importStart()" :type="importInProcessing ? 'danger' : 'success'" size="large" circle>
                            <el-icon size="28">
                                <SwitchButton />
                            </el-icon>
                        </el-button>
                    </el-progress>
                </el-col>

                <el-col :span="6">
                    <el-row>
                        <el-col>
                            <el-alert title="Импорт товаров" :type="importInfo.products.processed === importInfo.products.total ? 'success' : importInfo.products.processing ? 'warning' : 'info'" :closable="false">
                                <div>{{ importInfo.products.processed }} / {{ importInfo.products.total }} обработано</div>
                                <el-progress :percentage="importInfo.products.processed / importInfo.products.total * 100" :show-text="false" />
                            </el-alert>
                        </el-col>

                        <el-col>
                            <el-alert title="Импорт вариаций" :type="importInfo.variations.processed === importInfo.variations.total ? 'success' : importInfo.variations.processing ? 'warning' : 'info'" :closable="false">
                                <div>{{ importInfo.variations.processed }} / {{ importInfo.variations.total }} обработано</div>
                                <el-progress :percentage="importInfo.variations.processed / importInfo.variations.total * 100" :show-text="false" />
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
                    <el-tag>Seed {{ seed }}</el-tag>
                </el-col>

                <el-col :span="8">
                    {{ version }}
                </el-col>
            </el-row>
        </el-footer>
    </el-container>
</template>

<script setup>
    import { SwitchButton } from '@element-plus/icons-vue';
    import { v4 as uuid } from 'uuid';
    import { computed, reactive } from 'vue';

    const seed = uuid();
    const version = 'v1.0.0';

    const importInfo = reactive({
        step: null,

        categories: {
            processing: false,
            processed: 0,
            total: 79,
        },

        images: {
            processing: false,
            processed: 0,
            total: 300,
        },

        products: {
            processing: false,
            processed: 0,
            total: 50000,
        },

        variations: {
            processing: false,
            processed: 0,
            total: 50000,
        },
    });

    const steps = [
        {
            title: 'Категории',
            description: 'Импорт категорий',
        },
        {
            title: 'Изображения',
            description: 'Импорт изображений',
        },
        {
            title: 'Товары',
            description: 'Импорт товаров',
        },
        {
            title: 'Предложения',
            description: 'Импорт вариаций',
        },
        {
            title: 'Оптимизация',
            description: 'Оптимизация БД',
        },
    ];

    const importInProcessing = computed(() => importInfo.step !== null && importInfo.step === steps.length);

    const importStart = () => {
        importInfo.step = 0;
        importInfo.categories.processing = true;
    };

    const importStop = () => {
        importInfo.step = null;
        importInfo.categories.processing = false;
    };
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

    .el-alert--warning {
        --el-alert-bg-color: var(--el-color-primary-light-9);
        background-color: var(--el-alert-bg-color);
        color: var(--el-color-info);
    }

    .el-alert--warning:deep(.el-alert__description) {
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