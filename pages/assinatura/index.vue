<script setup>
    //funçao useFetch vai chamar o backend como se fosse o Insomnia
    const { data:subFound } = 
    await useFetch('http://localhost:8000/assinatura');
    key: 'subRequest'
</script>

<template>
    <div>    
        <h1>ASSINATURAS</h1>
        <h4>Aqui você pode ver as assinaturas disponíveis para os nossos planos!</h4><br>
        <section v-for="assinatura in subFound" 
        :key="assinatura.id">
            <h3>{{ assinatura.nome }} - {{ assinatura.valor }} </h3>
        </section>   
    </div>
</template>