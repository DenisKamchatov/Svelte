<script>
    import { Link } from 'svelte-navigator'

    const posts = localStorage.getItem('posts') ? JSON.parse(localStorage.getItem('posts')) : []

</script>

<ul class="list">
    {#if posts.length}
        {#each posts as post}
            <li class="list-item">
                <div class="item-block">
                    <h3 class="item-title">{post.title}</h3>
                    <div class="item-description">
                        <p>Создан: {post.createdAt}</p>
                        <p>Отредактирован: {post.editAt}</p>
                    </div>
                </div>
                <div class="item-buttons">
                    <Link to="/post/{post.id}">Открыть</Link>
                    <Link to="/editPost/{post.id}">Редактировать</Link>
                </div>
            </li>
        {/each}
        {:else}
        <p>Посты отсутствуют :(</p>
    {/if}
    
    
</ul>

<style>
    .list {
        list-style: none;
        background-color: #fff;
        box-shadow: 10px 5px 5px #4848481d;
        width: fit-content;
        margin: 30px auto 0 auto;
        padding: 20px;
        display: flex;
        flex-direction: column;
        align-items: center;
        border-radius: 10px;
    }
    .list-item {
        border: 1px solid rgb(93, 93, 93);
        border-radius: 10px;
        padding: 10px;
    }
    .list-item:not(:first-of-type) {
        margin: 15px 0 0 0;
    }
    .item-block {
        display: flex;
    }
    .item-description {
        margin: 0 0 0 15px;
    }
    .item-buttons {
        display: flex;
        justify-content: space-between;
        margin: 10px 0 0 0;
    }
</style>