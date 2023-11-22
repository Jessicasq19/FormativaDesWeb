<script setup>
    //funçao useFetch vai chamar o backend como se fosse o Insomnia
    const { data:subFound } = 
    await useFetch('http://localhost:8000/favoritos/');
    key: 'subRequest'
</script>

<template>
    <div>    
        <h1>OS FAVORITOS</h1>
        <h4>Aqui você pode ver quais são os queridinhos de nossos usuários!</h4><br>
        <section v-for="favoritos in subFound" 
        :key="favoritos.id">
            <h3>{{ favoritos.idUsuarioFK.nome }} - {{ favoritos.idFilmeFK.nome }} </h3>
        </section>   
    </div>
</template>