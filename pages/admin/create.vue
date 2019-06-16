<template>
    <div class="page-wrap">  
        <h2 class="mb">Создать новый пост</h2>     
       <el-form 
        :model="controls" 
        :rules="rules" 
        ref="form"
        @submit.native.prevent="onSubmit"
        >
        <el-form-item label="Введите название поста" prop="title">
            <el-input 
            v-model.trim="controls.title" 
            />
        </el-form-item>

        <el-form-item label="Текст в формате .md или в .html:" prop="text">
            <el-input 
            type="textarea"
            v-model="controls.text" 
            resize="none"
            :rows="10"
            />
        </el-form-item>
        <el-button class="mb" type="success" plain @click="previewDialog = true">Предпросмотр</el-button>
        <el-dialog
            title="Предпросмотр"
            :visible.sync="previewDialog">
            <div :key="controls.text">
                <vue-markdown>{{controls.text}}</vue-markdown>
            </div>
            </el-dialog>
        <el-form-item>
            <el-button 
                type="primary" 
                native-type="submit"
                round
                :loading="loading"
            >
            Создать пост</el-button>
        </el-form-item>
        </el-form>
    </div>
</template>

<script>
export default {
    layout: 'admin',
    head() {
        return {
            title: `Создать новый пост`
        }
    },
    data() {
        return {
            loading: false,
            previewDialog: false,
            controls: {
                title: '',
                text: '',
            },
            rules: {
                text: [
                    { required: true, message: 'Текст не должен быть пустым', trigger: 'blur' }
                ],
                title: [
                    { required: true, message: 'Название поста не может быть пустым', trigger: 'blur' }
                ],
            }
        }
    },
    methods: {
        onSubmit() {
            this.$refs.form.validate(async valid => {
                if (valid) {
                    this.loading = true

                    const formData = {
                        text: this.controls.text,
                        title: this.controls.title
                    }
                    try {         
                        await this.$store.dispatch('post/create', formData)
                        this.controls.title = ''
                        this.controls.text = ''
                        this.$message.success('Пост добавлен')
                    } catch(e) {}  finally { 
                        this.loading = false
                    }
                 
                } 
            });
        }
    }
}
</script>

<style lang="scss" scoped>
    .page-wrap {
        max-width: 600px;
    }
    .margin-rigth {
        margin-right: 2rem;
    }
</style>
