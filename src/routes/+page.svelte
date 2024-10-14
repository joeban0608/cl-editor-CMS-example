<script lang="ts">
	import Editor from 'cl-editor';

	// Define the types for the editor and HTML content
	let html: string = '<h3>hello</h3>';
	let editor: Editor | undefined; // editor is initially undefined

	// Handle the change event with the correct type for evt.detail
	const handleEditorChange = (evt: CustomEvent<string>) => {
		html = evt.detail;
	};
</script>

<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>

<Editor {html} on:change={handleEditorChange} />

<h1>Preview:</h1>
{@html html}
