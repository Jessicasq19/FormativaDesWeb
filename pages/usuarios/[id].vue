<script setup>
    const route = useRoute();

    const {data: usuariosFound} = 
    await useFetch(`http://localhost:8000/usuarios/${route.params.id}`,{
        key: 'usuariosRequest'
    });

    let showForm = false;
    const setShowForm = () => {
        //alert("Cliquei no botão!")
        showForm = true;
        refreshNuxtData()
    }   

    let nome;
    let cpf;
    let nascimento;
    let email;
    let fone;
    let foto;
    let idUserFK;
    let idAssinaturaFK;
    
    const saveUsuarios = async () => {
    await useFetch('http://localhost:8000/usuarios/',{
            method: 'GET',
            //lado esquerdo é o mesmo do backend,
            //lado direito é a variável do front
            body: {  
                nome: nome,
                cpf: cpf,
                nascimento: nascimento,
                email: email,
                fone: fone,
                foto: foto,
                idUserFK: idUserFK,
                idAssinaturaFK: idAssinaturaFK,
            },
            key: 'usuariosGet'            
        });

        alert("Mostrando os usuários");
}


    const saveUsuario = async () => {
    await useFetch('http://localhost:8000/usuarios/',{
            method: 'POST',
            //lado esquerdo é o mesmo do backend,
            //lado direito é a variável do front
            body: {  
                nome: nome,
                cpf: cpf,
                nascimento: nascimento,
                email: email,
                fone: fone,
                foto: foto,
                idUserFK: idUserFK,
                idAssinaturaFK: idAssinaturaFK,
            },
            key: 'usuariosPost'            
        });

        alert("Usuario saved!");
}
</script>

<template>
    <div>       
        <h1> Usuario: {{ usuariosFound.nome }} </h1>
        <p> Foto: {{ usuariosFound.foto }} </p>
    </div>    
</template>