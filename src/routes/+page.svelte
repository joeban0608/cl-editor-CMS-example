<script lang="ts">
	import EditorComponent from 'cl-editor/src/Editor.svelte';
	import { SvelteComponentTyped } from 'svelte';

	// 为 Editor 组件定义类型
	interface EditorProps {
		html: string;
	}

	interface EditorEvents {
		change: CustomEvent<string>;
	}

	const Editor = EditorComponent as unknown as typeof SvelteComponentTyped<
		EditorProps,
		EditorEvents
	>;

	// 初始化 html
	let html: string = '<h3>hello</h3>';

	// 处理 change 事件
	const handleEditorChange = (evt: CustomEvent<string>) => {
		html = evt.detail;
	};
</script>

<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>

<!-- 使用手动定义的 Editor 组件 -->
<Editor {html} on:change={handleEditorChange} />

<h1>Preview:</h1>
{@html html}
