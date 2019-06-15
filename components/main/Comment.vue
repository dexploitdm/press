<template>
    <el-card class="comment">
        <div class="comment-header">
            <span>Person man</span>
            <span>
                <i class="el-icon-watch"></i>
                {{ new Date().toLocaleString()}}
            </span>
        </div>
        <div class="comment-text">
            fgsdthh shrth stfhrs
        </div>
    </el-card>
</template>

<script>
export default {
    props: ['comment']
}
</script>

<style lang="scss" scoped>
    .comment {
        margin-bottom: 1rem;
    }
    .comment-header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 0.5rem;
        font-size: 0.8rem;
    }
    .comment-text {
        white-space: pre-line;
    }
</style>