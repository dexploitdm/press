<template>
    <el-card 
    shadow="hover"
    :body-style="{padding: 0}"
    class="post"
    >
    <header slot="header" class="post-header">
        <h3>Post title</h3>
        <small>
            <i class="el-icon-watch"></i>
            {{ new Date().toLocaleString()}}
        </small>
    </header>
    <div class="post-body">
        <img 
        src="https://i.pinimg.com/originals/14/cf/f9/14cff9039fe1becf61a9ece3ce7d2d4a.jpg" 
        alt="post image" 
        class="post-image">
    </div>
    <footer class="post-footer">
        <el-button round @click="openPost">Открыть пост</el-button>
        <span>
            <i class="el-icon-chat-dot-square"></i>
            12
        </span>
    </footer>
    </el-card>
</template>
 
<script>
export default {
    methods: {
        openPost() {
            const id = 'test-id'
            this.$router.push(`/post/${id}`)
        }
    }
}
</script>

<style lang="scss" scoped>
    .post {
        margin-bottom: 1.5rem;
    }
    .post-header {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    .post-image {
        width: 100%;
        height: auto;
    }
    .post-footer {
        padding: 1rem;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
</style>