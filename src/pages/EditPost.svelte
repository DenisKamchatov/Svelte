<script>
    import Form from "../components/Form.svelte";

    export let postId;
</script>


<main class="main">
    <Form edit={true} postId={postId} />
</main>