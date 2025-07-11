<template>
    <div>
        <h1>Tasks tracker</h1>
        <ButtonComp text="Add Task" color="green" />
    </div>
</template>

<script>
import ButtonComp from '../TasksTracker/ButtonComp.vue'

export default {
    name: 'TasksTracker',
    components: {
        ButtonComp
    }
}
</script>
