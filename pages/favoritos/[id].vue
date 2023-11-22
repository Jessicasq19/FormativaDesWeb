<script setup>
    const route = useRoute();

    const {data: favoritosFound} = 
    await useFetch(`http://localhost:8000/favoritos/${route.params.id}`,{
        key: 'favoritosRequest'
    });

    let showForm = false;
    const setShowForm = () => {
        //alert("Cliquei no botão!")
        showForm = true;
        refreshNuxtData()
    }   

    let usuario;
    let filme;
    
    const saveFavorito = async () => {
    await useFetch('http://localhost:8000/favoritos/',{
            method: 'GET',
            //lado esquerdo é o mesmo do backend,
            //lado direito é a variável do front
            body: {  
                idUsuarioFK: usuario, 
                idFilmeFK: filme, 
            },
            key: 'favoritosGet'            
        });

        alert("Mostrando os favoritos");
}


    const saveFavoritos = async () => {
    await useFetch('http://localhost:8000/favoritos/',{
            method: 'POST',
            //lado esquerdo é o mesmo do backend,
            //lado direito é a variável do front
            body: {  
                idUsuarioFK: 1, 
                idFilmeFK: route.params.id, //trip que foi selecionada 
            },
            key: 'favoritosPost'            
        });

        alert("Favorito saved!");
}
</script>

<template>
    <div>       
        <h1> Filme: {{ favoritosFound.idFilmeFK }} </h1>
        <p> Usuario: R${{ favoritosFound.idUsuarioFK }} </p>
    </div>    
</template>