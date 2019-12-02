<template>
  <div class="post-item">
    <div class="post-content">
      <div class="post-header">
        <span class="user-avatar"></span>
        <h3>{{ post.title }}</h3>
      </div>
      <div class="post-body">
        {{ post.body }}
      </div>
      <div class="post-footer">
        <a class="btn btn-primary" href="#">View More</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PostItem',
  props: {
    post: Object
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .post-item {
    display: flex;
    flex-wrap: wrap;
    padding: 0 15px;
    margin-bottom: 30px;
    width: 50%;
  }

  .post-item .post-content {
    display: flex;
    flex-wrap: wrap;
    flex-direction: column;
    border-radius: 7px;
    border: 1px solid rgba(0, 0, 0, 0.15);
    box-shadow: 0px 3px 5px rgba(0, 0, 0, 0.2);
  }
  
  .post-item .post-header {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    background: rgba(0, 0, 0, 0.05);
    padding: 10px 15px;
    border-radius: 7px 7px 0 0;
    border-bottom: 1px solid #cccccc;
  }
  .post-item .post-header .user-avatar {
    width: 40px;
    height: 40px;
    border-radius: 100%;
    border: 1px solid #007bff;
  }
  .post-item .post-header h3 {
    text-align: center;
    font-size: 14px;
    margin: 0;
    width: calc(100% - 40px);
  }

  .post-item .post-body {
    padding: 15px;
    font-size: 14px;
  }

  .post-item .post-footer {
    display: flex;
    flex-wrap: wrap;
    align-self: flex-end;
    justify-content: center;
    margin: auto 0 0 0;
    width: 100%;
    padding: 7px 15px;
    border-top: 1px solid #cccccc;
    border-radius: 0 0 7px 7px;
  }
</style>
