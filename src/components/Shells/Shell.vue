<template >
    <div class="shell-detail">
        <a-form
            ref="formRef"
            name="dynamic_form_nest_item"
            :label-col="labelCol"
            :wrapper-col="wrapperCol"
            :model="shellState"
            @finish="onFinish"
        >
            <a-form-item
                label="Shell Name"
                name="name"
                :rules="[{ required: true, message: 'Please input shell name!' }]"
            >
                <a-input v-model:value="shellState.name" />
            </a-form-item>
            <a-space
                v-for="(env, index) in shellState.envs"
                :key="env.id"
                style="display: flex; margin-bottom: 8px; width: 100%;"
                align="baseline"
            >
                <a-form-item
                    :name="['envs', index, 'key']"
                    :label="index === 0 ? 'Shell Env' : ' '"
                    :rules="{
                        required: true,
                        message: 'Missing key',
                    }"
                >
                    <a-input v-model:value="env.key" placeholder="key" />
                </a-form-item>=
                <a-form-item
                    :name="['envs', index, 'value']"
                    :wrapper-col="{
                        span: 36
                    }"
                    :rules="{
                        required: true,
                        message: 'Missing value',
                    }"
                >
                    <a-input v-model:value="env.value" placeholder="value" />
                </a-form-item>
                <MinusCircleOutlined @click="removeEnv(env)" />
            </a-space>
            <a-form-item>
                <a-button type="dashed" block @click="addEnv">
                    <PlusOutlined />Add user
                </a-button>
            </a-form-item>
            <a-form-item>
                <a-button type="primary" html-type="submit">Submit</a-button>
            </a-form-item>
        </a-form>
        <div class="editor-container">
            <Editor :content="content" :language="language"></Editor>
        </div>
    </div>
</template>
<script setup lang="ts">
import Editor from '@/components/Monaco/Editor.vue';
import { reactive, ref, UnwrapRef, toRaw } from 'vue';
import type { FormInstance } from 'ant-design-vue';
import { MinusCircleOutlined, PlusOutlined } from '@ant-design/icons-vue';

const content = ['function x() {', '\tconsole.log("Hello world!");', '}'].join('\n')
const language = 'javascript'

const labelCol = { style: { width: '150px' } }
const wrapperCol = { span: 14 }

interface Env {
    key: string;
    value: string;
    id: number;
}

interface ShellState {
    name: string;
    envs: Env[];
}

const shellState = reactive<ShellState>({
    name: '',
    envs: [{
        key: '',
        value: '',
        id: Date.now(),
    }]
});

const formRef = ref<FormInstance>();

// 添加环境
const addEnv = () => {
    shellState.envs.push({
        key: '',
        value: '',
        id: Date.now(),
    });
};

// 移除环境
const removeEnv = (item: Env) => {
    let index = shellState.envs.indexOf(item);
    if (index !== -1) {
        shellState.envs.splice(index, 1);
    }
};

const onFinish = (values: any) => {
    console.log('Received values of form:', values);
    console.log('dynamicValidateForm.users:', shellState.envs);
};

</script>

<!-- <style lang="scss" scoped>
.shell-detail {
    background: white;
    width: 80%;
    margin: 0;

    .ant-input {
        border-bottom: 1px solid #dbdbdb;
        border-top: 0px;
        border-left: 0px;
        border-right: 0px;
        border-radius: 0px;
    }
    textarea,
    textarea.ant-input:hover,
    textarea:focus {
        border: 1px solid #dae2f3;
        -webkit-box-shadow: none;
        box-shadow: none;
    }

    .ant-row {
        /*设置为伸缩容器*/
        display: -webkit-box;
        display: -moz-box;
        display: -ms-flexbox;
        display: -webkit-flex;
        display: flex;
        /*垂直居中*/
        -webkit-box-align: center; /*旧版本*/
        -moz-box-align: center; /*旧版本*/
        -ms-flex-align: center; /*混合版本*/
        -webkit-align-items: center; /*新版本*/
        align-items: center; /*新版本*/
    }
    .editor-container {
        padding: 20px;
    }
}
</style> -->