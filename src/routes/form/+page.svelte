<script lang="ts">
	import { AirNotice } from 'airnotice-events';

	function handleSubmit() {
		AirNotice.event('submit form', 'form', {}, true);
	}
</script>

<form>
	<label for="">Your name</label>
	<input type="text" placeholder="John doe" />

	<label for="">Your name</label>
	<input type="text" placeholder="John doe" />

	<label for="">Your name</label>
	<input type="text" placeholder="John doe" />

	<button type="button" onclick={handleSubmit}>Submit</button>
</form>

<style>
	form {
		display: flex;
		flex-direction: column;
		gap: 30px;
		width: 30%;
	}

	input {
		background: #222222;
		color: white;
	}

	button {
		background: #222222;
		color: white;
	}
</style>
