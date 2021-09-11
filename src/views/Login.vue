<script setup lang="ts">
    import { sha256 } from 'js-sha256';

    const vocab = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789~_.-";

    const gen_verifier = function() {
        var output = "";
        for (var i = 0; i < 43; ++i)
        {
            output += vocab[Math.floor(Math.random() * 43)];
        }
        return output;
    }

    const gen_challenge = function(v) {
        return btoa(sha256.hex(v));
    }

    const redir_spotify = function() {
        const challenge = gen_challenge(gen_verifier());

        alert(challenge);

        window.location.replace("https://accounts.spotify.com/authorize?client_id=295da56c9fb14e10a173a5fac6a3ba4f&response_type=code&redirect_uri=http://localhost:3000/auth.html&code_challenge_method=S256&code_challenge=" + challenge);
    }
</script>

<template>
    Welcome to login

    <div id="login-button" @click="redir_spotify()">
        login
    </div>
</template>

<style>
    #login-button {
        padding: 10px;
        background-color: #00aa00;
        color: #ffffff;
        cursor: pointer;
    }
</style>
