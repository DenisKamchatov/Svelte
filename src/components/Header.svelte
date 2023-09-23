<script>
	import { Link } from 'svelte-navigator'

</script>

<header class="header">
    <Link to="/">Список постов</Link>
    <Link to="create">Создать пост</Link>
</header>

<style>
    .header {
        display: flex;
        align-items: center;
        justify-content: center;
        padding: 20px 0;
        background-color: rgb(212, 212, 212);
        gap: 30px;
    }
</style>