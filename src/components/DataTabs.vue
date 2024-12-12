<template>
    <div class="tabs-container">
        <div class="tab" v-for="tab in tabs" :key="tab" :class="{ active: currentTab === tab }" @click="updateTab(tab)">
            {{ tab }}
        </div>
    </div>
</template>

<script>
export default {
    props: ['currentTab'], 
    methods: {
        updateTab(tab) {
            if (this.currentTab !== tab) {
                this.$emit('update-tab', tab);
            }
        }
    },
    data() {
        return {
            tabs: ['Standings', 'Players', 'Matches']
        };
    }
};
</script>

<style scoped>
.tabs-container {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: auto;
    gap: 10px;
    justify-content: center;
    align-items: center;
    margin: 20px 0;
}

.tab {
    padding: 10px 20px;
    font-size: 1rem;
    font-weight: bold;
    color: #555;
    background-color: #f0f0f0;
    border: 1px solid #ccc;
    border-radius: 20px;
    text-align: center;
    cursor: pointer;
    transition: all 0.3s ease;
}

.tab:hover {
    background-color: #e0f7fa;
    color: #007b83;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.tab.active {
    background-color: #007b83;
    color: white;
    border: 1px solid #005a60;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.tab:focus {
    outline: none;
}

@media (max-width: 600px) {
    .tabs-container {
        grid-template-columns: 1fr;
        gap: 5px;
    }

    .tab {
        width: 100%;
        padding: 15px 10px;
        font-size: 1.1rem;
    }
}
</style>
