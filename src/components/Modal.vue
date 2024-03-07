<template>
    <!-- Emitting custom events -->
    <!-- <div class="backdrop" @click="closeModal"> -->
    
        <!-- Click event modifiers(.self) -->
    <div class="backdrop" @click.self="closeModal">
        <!-- Added dynamic themes -->
        <div class="modal" :class="{ short: theme === 'short'}">
            
            <!-- <h1>Modal Style Clash</h1> -->
            
            <!-- <h1>{{heading}}</h1>
            <p>{{text}}</p> -->

            <!-- Slots -->
            <!-- Default Slot -->
            <slot>
                <!-- default content only shows when no default contents is passed from the parent component -->
            </slot>
            
            <!-- named slots -->
            <div class="actions">
                <slot name="links"></slot>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    // props: ['heading', 'text', 'theme'],
    
    // Slots
    props: ['theme'],
    
    // Emitting custom events
    methods: {
        closeModal() {
            this.$emit('close')
        }
    }
}
</script>

<!-- override modal style clash #1 -->
<style>
.backdrop{
    top: 0;
    position: fixed;
    background: rgba(0,0,0,0.5);
    width: 100%;
    height: 100%;
}
.modal {
    width: 400px;
    padding: 20px;
    margin: 100px auto;
    background: white;
    border-radius: 10px;
}
/* override modal style clash #1 */
h1 {
    color: aqua;
    border: none;
    padding: 0;
}
/* override global style */
.modal p {
    font-style: normal;
}
.modal .actions {
    text-align: center;
    margin: 30px 0 10px 0;
    
}
.modal .actions a{
    border-radius: 4px;
    margin: 10px;
    color: #333;
    padding: 8px;
    border: 1px solid #eee;
    text-decoration: none;
}
/* Styling theme(short) prop */
.modal.short{
    background: crimson;
    color: white;
}
.modal.short h1{
    color: white;
}
.modal.short .actions{
    color: white;
}
.modal.short .actions a{
    color: white;
}
</style>


<!-- override modal style clash #2  -->
<!-- <style>
.modal h1 {
    color: aqua;
    border: none;
    padding: 0;
}
</style> -->