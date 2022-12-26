<template>
    <div class="app">
        <div>
            <form>
                <h4>Создание поста</h4>
                <input 
                v-model="title"
                class="input" 
                type="text" 
                placeholder="Название">
                <input 
                v-model="body"
                class="input" 
                type="text" 
                placeholder="Описание">
                <button class="btn" @click.prevent="createPost">Создать</button>
            </form>
        </div>
     <div class="post" v-for="(post,index) in posts">
        <div><strong>Название:</strong>{{post.title}}</div>
        <div><strong>Описание:</strong>{{post.body}}</div>
        <button class="btn"  @click.prevent= "deletePost(index)">Удалить</button>
     </div>
    </div>
</template>

<script>
export default {
    data:() => ({
        posts: [
                {id: 1, title:'Заголовок', body: 'Описание поста' },
                {id: 2, title:'Заголовок 2', body: 'Описание поста 2' },
                {id: 3, title:'Заголовок 3', body: 'Описание поста 3 ' },
            ],
        title: '',
        body: '',
}),

    methods: {
        createPost (event) {
            const newPost = {
                id: Date.now(),
                title: this.title,
                body: this.body,
            }
            this.posts.push(newPost)
            this.title = ''
            this.body = ''
        },
        deletePost(index) {
            this.posts.splice(index,1)
        }
    }
}


</script>
