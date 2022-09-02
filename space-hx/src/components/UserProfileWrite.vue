<template>
    <div class="card edit-field">
        <div class="card-body">
            <div class="mb-3">
                <label for="edit-post" class="form-label">编辑区</label>
                <textarea v-model="content" class="form-control" id="edit-post" rows="3"></textarea>
                <button @click="post_submit" type="button" class="btn btn-primary btn-sm">发帖</button>
            </div>
        </div>
    </div>
</template>

<script>
import { ref } from 'vue';
export default {
    name: "UserProfileWrite",
    setup(props, context) {
        const post_submit = () => {
            context.emit('post_submit', content.value);
            content.value = "";

        }
        let content = ref('')
        return {
            content: content,
            post_submit,
        }
    }
}
</script>

<style scoped>
.edit-field {
    margin-top: 20px;
}

button {
    margin-top: 10px;
}
</style>