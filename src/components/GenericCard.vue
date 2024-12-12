<template>
    <div class="card">
        <h3>{{ data.name || data.homeTeam || data.team }}</h3>
        <div class="card-content">
            <div class="card-row" v-for="(value, key) in formattedData" :key="key">
                <p v-if="typeof value !== 'object' && !Array.isArray(value)">
                    <strong>{{ formatKey(key) }}:</strong> {{ value }}
                </p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ['data'],
    computed: {
        formattedData() {
            return Object.fromEntries(
                Object.entries(this.data)
                    .filter(([key]) => key !== '__v') 
                    .map(([key, value]) => [
                        key === '_id' ? 'Id' : key, 
                        value
                    ])
            );
        }
    },
    methods: {
        formatKey(key) {
            return key
                .replace(/([A-Z])/g, ' $1')
                .replace(/^./, str => str.toUpperCase());
        }
    }
};
</script>

<style scoped>
.cards-container {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    grid-template-rows: auto;
    gap: 15px;
    padding: 20px;
}


@media (max-width: 600px) {
    .cards-container {
        grid-template-columns: 1fr;
        grid-template-rows: auto;
    }
}

.card {
    border: 1px solid #ddd;
    padding: 20px;
    background-color: #f9f9f9;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    border-radius: 8px;
    transition: transform 0.3s, box-shadow 0.3s;
    margin: 10px;
    text-align: center;
}

/* Hover effect */
.card:hover {
    transform: translateY(-5px);
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
    background-color: #e0f7fa;
}

.card h3 {
    font-size: 1.4rem;
    margin-bottom: 15px;
    text-align: center;
    font-weight: bold;
}

.card-content {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 10px;
}

.card-row {
    display: flex;
    flex: 0 1 calc(33.33% - 10px);
    justify-content: center;
    align-items: center;
    text-align: center;
    margin-bottom: 10px;
    font-size: 0.95rem;
}

.card-row p {
    margin: 0;
}

@media (max-width: 600px) {
    .card-row {
            flex: 0 1 100%;
        }
}
</style>
