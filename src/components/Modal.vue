<template>
    <section class="backDrop" @click.self="closeModale">
       
        <div class="modal" :class="{ sale: theme === 'sale' }">
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
            closeModale (){ //emettre un event qui sera écouté par le parent
                this.$emit('EcloseModale')
            }
        }
    }
</script>


<style>
    .modal{
        width: 400px;
        padding: 20px;
        margin: 100px auto;
        background-color: white;
        border-radius: 10px;
        
    }
    .backDrop{
        position: fixed;top: 0;left: 0;
        background-color: rgba(0, 0, 0, 0.493);
        width: 100%;
        height: 100%;
    }
    .modal h1{
        color: white;
    }
    .modal.sale{
        color: white;
        background: #FF4E50;  /* fallback for old browsers */
        background: -webkit-linear-gradient(45deg, #F9D423, #FF4E50);  /* Chrome 10-25, Safari 5.1-6 */
        background: linear-gradient(45deg, #F9D423, #FF4E50); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */

    }
    .modal .links{
        display: flex;
        flex-direction: column;
        
    }
    .modal .links a{
        padding: 5px;
        background: rgba(255, 255, 255, 0.438);
        width: 50%;
        margin: 3px auto;
        border-radius: 6px;
        color: white;
        text-decoration: none;
    }
    


</style>