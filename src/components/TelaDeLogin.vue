<template >


<div class="controleTela">

    <p class="controleTela__texto">Controle de acesso: </p>
    

    <div class="controleInput">

        <p class="controleInput__titulo">Tela de Login</p>

        <input type="text" placeholder="Nome de Usuário" v-model="usuario" class="controleInput__estilo">
        <input type="password" placeholder="Senha" v-model="senha" class="controleInput__estilo">
        <input type="password" placeholder="Confirmar Senha"  v-model="confirmaSenha" class="controleInput__estilo">

        <div class="controleButton">
        <button class="controleButton__estilo" @click="verificaLogin()">Login</button>

    </div>

    <p :style="{fontSize: '1.9rem !important'}" v-html="logado"></p>


    </div>

    <div class="controleLista" v-if="ativo">
        <p class="controleLista__texto">Acessos liberados para essa conta</p>

        <ul>
            <li v-for="acesso in acessos" :key="acesso"> {{ acesso }} </li>
        </ul>

    </div>


</div>

</template>


<script>

export default{

    data(){

        return {

            usuario: '',
            senha: '',
            confirmaSenha: '',
            logado: '',
            acessos: ['Admin |', 'Gerente |', 'Lojista |', 'Vendedor'],
            ativo: false
            
        }

    },

    methods: {

        verificaLogin(){

            const senha = this.senha;
            const confirmaSenha = this.confirmaSenha;
    
          
            if(senha === confirmaSenha && this.usuario != '' && senha != ''){


                this.logado = 'Usuário Logado: ' + this.usuario;
                this.ativo = true

            }else if(senha != confirmaSenha){
                
                this.logado = 'Login ou Senhas incorretos.'

            }else{

                this.logado = 'Dados não informados'

            }
           
        }

    },

    mounted(){

        setTimeout(() => {

            this.usuario = '',
            this.senha = '',
            this.confirmaSenha = ''
            this.ativo = false
            this.logado = 'Login expirado'

        }, 120000)

        setTimeout(() => {
            this.logado = ''
        }, 130000)

    }

}

</script>


<style scoped>



.controleTela{

    display: flex;
    flex-direction: column;
    justify-content: center;

}

.controleInput{

    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    align-self: center;
    width: 25rem;
    gap: 10px;
    border: 10px solid #863B1E;
    border-radius: 30px;
    background-color: #A06D58;
    transform: translateY(70%);
  

}

.controleInput__estilo{

    text-align: center;
    font-size: 1.3rem;
    font-family: Arial, Helvetica, sans-serif;
    font-weight: 600;
}

.controleInput__titulo{

    text-align: center;
    font-size: 1.5rem;
    font-weight: 600;
    font-family: Arial, Helvetica, sans-serif;

}

.controleButton{

    display: flex;
    flex-direction: row;
    justify-content: center;

}

.controleButton__estilo{

    width: 6rem;
    height: 2rem;
    margin-top: 1%;
    text-transform: uppercase;
    font-weight: 600;
    font-size: 1.2rem;
    background-color: bisque;
    font-family: Arial, Helvetica, sans-serif;

}

li{
    list-style: none;
}

ul{
    display: flex;
    flex-direction: row;
    justify-content: center;
    gap: 10px;
    font-size: 2rem;
    font-family: Arial, Helvetica, sans-serif;
    font-weight: 600;
}

.controleLista{

    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    align-self: center;
    position: relative;
    top: 20vw;
    font-family: Arial, Helvetica, sans-serif;
    border: 10px #4AEB2F solid;
    border-radius: 2px;
    background-color: #42E3D2;
    width: 40vw;

}


.controleLista__texto{

    text-align: center;
    font-size: 1.8rem;
    font-weight: 600;
    font-family: Arial, Helvetica, sans-serif;

}

.controleTela__texto{

    text-align: center;
    font-size: 3rem;
    font-family: Arial, Helvetica, sans-serif;
    font-weight: 600;
    transform: translateY(10vw);
    text-transform: uppercase;
    color: #E35842;

}

</style>