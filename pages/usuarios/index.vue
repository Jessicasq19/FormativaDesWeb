<script setup>
    //funçao useFetch vai chamar o backend como se fosse o Insomnia
    const { data:subFound } = 
    await useFetch('http://localhost:8000/usuarios/');
    key: 'subRequest'
</script>

<template>
    <div>    
        <h1>USUÁRIOS</h1>
        <h4>Aqui você pode ver quais são os nossos usuários!</h4><br>
        <section v-for="usuarios in subFound" 
        :key="usuarios.id">
            <h3>{{ usuarios.nome }}</h3>
        </section>   
    </div>
</template>