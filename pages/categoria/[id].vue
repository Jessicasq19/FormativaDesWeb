<script setup>
    const route = useRoute();

    const {data: categoriaFound} = 
    await useFetch(`http://localhost:8000/categoria/`,{
        key: 'categoriaRequest'
    });

    let showForm = false;
    const setShowForm = () => {
        //alert("Cliquei no botão!")
        showForm = true;
        refreshNuxtData()
    }   

    let nome;
    
    const saveCategoria = async () => {
    await useFetch('http://localhost:8000/categoria/',{
            method: 'GET',
            //lado esquerdo é o mesmo do backend,
            //lado direito é a variável do front
            body: {  
                nome: nome,
            },
            key: 'categoriaGet'            
        });

        alert("Todas as categorias");
}
</script>

<template>
    <div>       
        <h1>A categoria é: {{ categoriaFound.nome }} </h1>
    </div>    
</template>