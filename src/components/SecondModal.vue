<template>
    <section class="SbackDrop" @click.self="closeSignUpModale" >
       
        <div class="signUp" :class="{ black: theme === 'black' }">
            <!-- <h1>{{ titre }}</h1>
            <p>{{ text }}</p> Props -->
            <slot>
                default content 
            </slot>
            <div class="links">
                <slot name="links">
                    the content you write here in the slot is shown only if it doesn't receive anything
                </slot>
            </div>
            
        </div>
         
    </section>
</template>

<script>
    export default{
        props: [
            // "titre",
            // "text", Props
            "theme"
        ],
        methods: {
            closeSignUpModale (){ //emettre un event qui sera écouté par le parent
                this.$emit('EcloseScndModale')
            }
        }
    }
</script>


<style>


    .signUp{
        width: 400px;
        padding: 20px;
        margin: 100px auto;
        background-color: white;
        border-radius: 10px;
        color: black;
        
    }
    .SbackDrop{
        position: fixed;top: 0;left: 0;
        background-color: rgba(0, 0, 0, 0.493);
        width: 100%;
        height: 100%;
    }
    .signUp h1{
        color: black;
    }
    .black h1{
        color: white;
    }
    
    .black{
        color: white;
        
        background: #0F2027;  /* fallback for old browsers */
        background: -webkit-linear-gradient(45deg, #2C5364, #203A43, #0F2027);  /* Chrome 10-25, Safari 5.1-6 */
        background: linear-gradient(45deg, #2C5364, #203A43, #0F2027); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */


    }
    .signUp .links{
        display: flex;
        flex-direction: column;
        
    }
    .black .links a{
        padding: 5px;
        border: 2px solid white;
        width: 50%;
        margin: 3px auto;
        border-radius: 6px;
        color: white;
        text-decoration: none;
        text-align: center;
    }
    


</style>