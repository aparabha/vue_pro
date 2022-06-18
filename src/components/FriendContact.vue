<template>
<li>
    <h2>{{name}}{{friendIsFavorite ?'(Fovorite)':''}}</h2>
    <button v-on:click="toggleDetails()">{{ detailsAreVisible ? 'Hide ' : 'Show '}}Details</button>
    <button v-on:click="toggleFavorite()">Toggle favorite</button>
    <button v-on:click="$emit('delete',id)">Delete friend</button>
    <ul v-if="detailsAreVisible">
        <li><strong>Phone:</strong>{{phoneNumber}}</li>
        <li><strong>Email:</strong>{{emailAddress}}</li>
    </ul>
</li>
</template>
<script>
    export default{
        props:{
            name:{
                type:String,
                required:true

        },
            phoneNumber:{
                type:String,
                required:true
            },
            emailAddress:{
                type:String,
                required:true
            },
            isFavorite:{
                type:Boolean,
                required:false,
                default:false,
                // validator:function(value){
                //     return value =='1' || value =='0';

                // }
            }
        },
       emits:['delete'],
        data(){
            return{
                detailsAreVisible:false,
                friendIsFavorite:this.isFavorite,
            };
        },
        methods:{
            toggleDetails(){
                this.detailsAreVisible=!this.detailsAreVisible;
            },
            toggleFavorite(){
                this.friendIsFavorite=!this.friendIsFavorite;
                //this.$emit('toggle-favorite',this.id);
               
            }
            
        }
    };
</script>