<script>
	import { Route, Router } from 'svelte-navigator'
    import Header from './components/Header.svelte';
    import Main from './pages/Main.svelte';
    import CreatePost from './pages/CreatePost.svelte';
    import Post from './pages/Post.svelte';
    import EditPost from './pages/EditPost.svelte';
	// export let name;
</script>

<Router>
	<Header />

	<Route path='/'>
		<Main />
	</Route>
	<Route path='/create'>
		<CreatePost />
	</Route>
	<Route path='/editPost/:postId' let:params>
		<EditPost postId={params.postId} />
	</Route>
	<Route path='/post/:postId' let:params>
		<Post postId={params.postId} />
	</Route>
</Router>


