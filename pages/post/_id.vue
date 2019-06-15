<template>
  <article class="post">
    <header class="post-header">
      <div class="post-title">
        <h1>Post title</h1>
        <nuxt-link to="/">
            <i class="el-icon-d-arrow-left"></i>
        </nuxt-link>
      </div>
      <div class="post-info">
        <small>
          <i class="el-icon-watch"></i>
          {{ new Date().toLocaleString()}}
        </small>
        <small>
            <i class="el-icon-view"></i>
            42
        </small>
      </div>
      <div class="post-image">
          <img 
        src="https://i.pinimg.com/originals/14/cf/f9/14cff9039fe1becf61a9ece3ce7d2d4a.jpg" 
        alt="post image" 
        class="post-image">
      </div>
    </header>
    <main class="post-content">
        <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Amet officiis illo optio tempora reprehenderit rerum labore sit rem delectus magnam expedita vitae a magni, aut, sapiente consequatur? Cum, tempora! Praesentium?

        </p>
    </main>
    <footer>
      <app-comment-form 
        v-if="canAddComment"
        @created="createCommentHandler"
      />
      <div class="comments" v-if="true">
        <app-comment 
          v-for="comment in 4"
          :key="comment"
          :comment="comment"
        />
      </div>
      <div class="text-center" v-else>Комментариев нет</div>
    </footer>
  </article>
</template>

<script>
import AppComment from '~/components/main/Comment'
import AppCommentForm from '~/components/main/CommentForm'
export default {
  components: {
    AppComment, AppCommentForm
  },
  validate({ params }) {
    return Boolean(params.id);
  },
  data() {
    return {
      canAddComment: true
    }
  },
  methods: {
    createCommentHandler() {
      this.canAddComment = false
    }
  }
};
</script>

<style lang="scss" scoped>
.post {
    max-width: 600px;
    margin: 0 auto;
}
.post-title {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 1rem;
}
.post-info {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 0.5rem;
}
.post-image img {
    width: 100%;
    height: auto;
}
.post-header {
    margin-bottom: 1.5rem;
}
.post-content {
    margin-bottom: 2rem;
}
</style>