<script setup>
    const route = useRoute();

    const {data: assinaturaFound} = 
    await useFetch(`http://localhost:8000/assinatura/`,{
        key: 'assinaturaRequest'
    });

    let showForm = false;
    const setShowForm = () => {
        //alert("Cliquei no botão!")
        showForm = true;
        refreshNuxtData()
    }   

    let nome;
    let valor;
    
    const saveAssinatura = async () => {
    await useFetch('http://localhost:8000/assinatura/',{
            method: 'GET',
            //lado esquerdo é o mesmo do backend,
            //lado direito é a variável do front
            body: {  
                nome: nome, 
                valor: valor, 
            },
            key: 'assinaturaGet'            
        });

        alert("Todas as assinaturas");
}
</script>

<template>
    <div>       
        <h1>Essa é a Assinatura: {{ assinaturaFound.nome }} </h1>
        <p> Valor: R${{ assinaturaFound.valor }} </p>
    </div>    
</template>