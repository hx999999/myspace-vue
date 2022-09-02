<template>
    <ContentBase>
        <div class="row">
            <div class="col-3">
                <UserProfileInfo @follow="follow" @unfollow="unfollow" v-bind:user="user"></UserProfileInfo>
                <UserProfileWrite @post_submit="post_submit"></UserProfileWrite>
            </div>
            <div class="col-9">
                <UserProfilePosts :posts="posts"></UserProfilePosts>
            </div>
        </div>
    </ContentBase>
</template>

<script>
import ContentBase from '../components/ContentBase'
import UserProfileInfo from '../components/UserProfileInfo'
import UserProfilePosts from '../components/UserProfilePosts'
import UserProfileWrite from '../components/UserProfileWrite'
import { reactive } from 'vue'
export default {
    name: 'UserProfileView',
    components: {
        ContentBase,
        UserProfileInfo,
        UserProfilePosts,
        UserProfileWrite,
    },
    setup() {
        const user = reactive({
            id: 1,
            username: "hanxing",
            lastname: "han",
            firstname: "xing",
            followerCount: 0,
            if_followed: false,
        });
        const posts = reactive({
            count: 3,
            posts: [
                {
                    id: 1,
                    userId: 1,
                    content: "今天上了web课",
                },
                {
                    id: 2,
                    userId: 1,
                    content: "今天上了java课",
                }
                ,
                {
                    id: 3,
                    userId: 1,
                    content: "今天上了linux课",
                }
            ]
        });
        const follow = () => {
            if (user.if_followed) return;
            user.if_followed = true;
            user.followerCount++;
        };
        const unfollow = () => {
            if (!user.if_followed) return;
            user.if_followed = false;
            user.followerCount--;
        };
        const post_submit = (content) => {
            posts.count++;
            posts.posts.unshift({
                id: posts.count,
                userId: 1,
                content: content,
            })
        }
        return {
            user: user,
            follow, unfollow, posts, post_submit,
        }
    }

}
</script>

<script scoped>
</script>