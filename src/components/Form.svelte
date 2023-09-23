<script>
    import { v4 as uuid } from 'uuid';

    let title = ''
    let description = ''
    
    export let edit
    export let postId

    const formatter = new Intl.DateTimeFormat("ru", {
        day: "numeric",
        month: "long",
        year: "numeric",
        hour: "numeric",
        minute: "numeric",
    });
    const date = new Date()
    const dateRemake = formatter.format(date)

    let posts = localStorage.getItem('posts') ? JSON.parse(localStorage.getItem('posts')) : []

    let post = postId ? posts.find(post => post.id === postId) : {}

    let titlePost = post.title
    let descriptionPost = post.description

    const createOrEditPost = () => {

        if (edit) {
            const postsFiltered = posts.filter(item => item.id !== post.id)

            post.title = titlePost
            post.description = descriptionPost
            post.editAt = dateRemake

            postsFiltered.push(post)
            
            localStorage.setItem('posts', JSON.stringify(postsFiltered))
            alert('Пост изменен!')

        } else {
            const postForm = {
                id: uuid(),
                title: title,
                description: description,
                createdAt: dateRemake,
                editAt: dateRemake
            }
            posts.push(postForm)

            localStorage.setItem('posts', JSON.stringify(posts))
            alert('Пост создан!')
        }
        
    }

    const deletePost = () => {
        let posts = localStorage.getItem('posts') ? JSON.parse(localStorage.getItem('posts')) : []
        
        post = posts.find(post => post.id === postId)
            
        const postsFiltered = posts.filter(item => item.id !== post.id)

        localStorage.setItem('posts', JSON.stringify(postsFiltered))
        alert('Пост удален!')
    }
</script>

<form class="form">
    {#if edit && post}
        <input class="input input-title" type="text" bind:value={titlePost} placeholder={'Название'} />
        <textarea class="input input-description" bind:value={descriptionPost} name="story" rows="5" cols="33" placeholder={'Описание'}></textarea>
        <button on:click={createOrEditPost} type="button" class="button">Редактировать пост</button>
        <button on:click={deletePost} type="button" class="button">Удалить пост</button>

        {:else}
        
        <input class="input input-title" type="text" bind:value={title} placeholder={'Название'} />
        <textarea class="input input-description" bind:value={description} name="story" rows="5" cols="33" placeholder={'Описание'}></textarea>
        <button on:click={createOrEditPost} type="button" class="button">Создать пост</button>
    {/if}
</form>

<style>
    .form {
        background-color: #fff;
        box-shadow: 10px 5px 5px #4848481d;
        width: fit-content;
        margin: 30px auto 0 auto;
        padding: 20px;
        display: flex;
        flex-direction: column;
        align-items: center;
        width: 300px;
        border-radius: 10px;
    }
    .input {
        border-radius: 5px;
        width: 100%;
    }
    .input-description {
        margin: 10px 0 0 0;
        resize: none;
    }
    .button {
        width: 200px;
        padding: 10px;
        border-radius: 5px;
        margin: 10px 0 0 0;
    }
</style>