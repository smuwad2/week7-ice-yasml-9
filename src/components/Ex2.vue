<script>
    export default { 
        // Add code in appropriate places
        data() {
            return {
                items: ['keyboard', 'mouse', 'iPhone', 'macbook', 'adapter'],
                newItem: ""
            }
            
        },
        methods: {
            removeElement: function (index) {
                this.items.splice(index, 1);
            },
            addItem: function (item) {
                this.items.push(item);
            }
        }
    }
</script>

<template>

    <h2>Shopping Cart</h2>
    <!-- TODO: Add Code Here -->
    <ul>
        <li v-for="item, idx in items"> {{ item }}
            <button @click="removeElement(idx)">Delete!</button>
        </li>
    </ul>

    <input type="text" v-model="newItem"></input>
    <button @click="addItem(newItem)">Add!</button>
   
</template>
