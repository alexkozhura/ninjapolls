<script>
    let fields = { question: '', answerA: '', answerB: '' };

    const submitHander = () => {
        console.log(fields);
    }
</script>

<form on:submit|preventDefault={submitHander}>
    <div class="form-field">
        <label for="question">Poll Question:</label>
        <input type="text" id="question" bind:value={fields.question}>
    </div>
    <div class="form-field">
        <!-- We need the for field to link the label to the input -->
        <label for="answer-a">Answer A:</label>
        <input type="text" id="answer-a" bind:value={fields.answerA}>
    </div>
    <div class="form-field">
        <label for="answer-b">Answer B:</label>
        <input type="text" id="answer-b" bind:value={fields.answerB}>
    </div>
    <button>Add Poll</button>
</form>

<style>

</style>