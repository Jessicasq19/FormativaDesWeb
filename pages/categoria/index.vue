<script setup>
    //funçao useFetch vai chamar o backend como se fosse o Insomnia
    const { data:subFound } = 
    await useFetch('http://localhost:8000/categoria');
    key: 'subRequest'
</script>

<template>
    <div>    
        <h1>CATEGORIAS</h1>
        <h4>Aqui você pode ver as categorias disponíveis para assistir!</h4><br>
        <section v-for="categoria in subFound" 
        :key="categoria.nome">
            <h3>{{ categoria.nome }} </h3>
        </section>   
    </div>
</template>