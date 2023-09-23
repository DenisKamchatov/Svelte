<script>
    export let postId;

    const posts = localStorage.getItem('posts') ? JSON.parse(localStorage.getItem('posts')) : []
    const post = posts.find(post => post.id === postId)
    console.log(post)

</script>

<main class="main">
    <h3>{post.title}</h3>
    <p>{post.description}</p>
    <p>Дата создания поста: 
        <span>{post.createdAt}</span>
    </p>
    <p>Дата редактирования поста: 
        <span>{post.editAt}</span>
    </p>
</main>

<style>
    .main {
        background-color: #fff;
        box-shadow: 10px 5px 5px #4848481d;
        width: fit-content;
        margin: 30px auto 0 auto;
        padding: 20px;
        display: flex;
        flex-direction: column;
        align-items: center;
        width: 300px;
        text-align: center;
        border-radius: 10px;
    }
    .main p span {
        display: block;
    }

</style>