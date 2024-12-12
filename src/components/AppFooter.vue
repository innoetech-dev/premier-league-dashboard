<template>
    <footer class="app-footer">
        <nav class="footer-nav">
            <ul>
                <li><a href="#" @click.prevent="navigateToTab('Standings')">Standings</a></li>
                <li><a href="#" @click.prevent="navigateToTab('Players')">Players</a></li>
                <li><a href="#" @click.prevent="navigateToTab('Matches')">Matches</a></li>
            </ul>
        </nav>
        <p>&copy; 2024 Premier League Dashboard. All Rights Reserved.</p>
    </footer>
</template>

<script>
export default {
    methods: {
        navigateToTab(tab) {
            this.$emit('update-tab', tab);
        }
    }
};
</script>

<style scoped>
.app-footer {
    display: grid;
    grid-template-rows: auto auto;
    grid-template-columns: 1fr;
    background-color: #333;
    color: white;
    padding: 20px;
    text-align: center;
}

.app-footer .footer-nav {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 15px;
    margin-bottom: 10px;
}

.app-footer .footer-nav ul {
    list-style-type: none;
    padding: 0;
    margin: 0;
    display: contents;
}

.app-footer .footer-nav ul li a {
    color: #00c4cc;
    text-decoration: none;
    font-weight: bold;
    font-size: 1rem;
    transition: color 0.3s ease;
}

.app-footer .footer-nav ul li a:hover {
    color: #fff;
}

.app-footer p {
    font-size: 0.9rem;
    color: #bbb;
    margin: 0;
}

@media (max-width: 600px) {
    .app-footer .footer-nav {
        grid-template-columns: 1fr;
        gap: 10px;
    }
}
</style>
