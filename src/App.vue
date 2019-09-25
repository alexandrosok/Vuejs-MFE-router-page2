<template>
<div id="page2">
    <router-view></router-view>
</div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
    name: 'page2',
    data() {
        return {
            state: {
                count: 0
            }
        }
    },
    components: {
        HelloWorld
    },
    mounted() {
        var self = this;

        self.state = self.props.store.getState(); //Initialization
        self.props.globalEventDistributor.subscribe(function () {
            self.state = self.props.store.getState();
        });
    },
    methods: {
        increment() {
            this.props.globalEventDistributor.dispatch({
                type: 'INCREMENT'
            });
        },
        decrement() {
            this.props.globalEventDistributor.dispatch({
                type: 'DECREMENT'
            });
        },
        localIncrement() {
            this.props.store.dispatch({
                type: 'INCREMENT'
            });
        },
        localDecrement() {
            this.props.store.dispatch({
                type: 'DECREMENT'
            });
        }
    }
}
</script>

<style>
#page2 {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
