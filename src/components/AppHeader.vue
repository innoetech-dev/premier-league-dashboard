<template>
    <header class="app-header">
        <div class="logo">
            <img src="@/assets/soccer-ball.png" alt="Soccer Ball Logo" />
            <h1>Premier League Dashboard</h1>
        </div>
    </header>
</template>

<script>
export default {};
</script>

<style scoped>
.app-header {
    background-color: #007b83;
    color: white;
    padding: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    text-align: center;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.app-header .logo {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 10px;
}

.app-header .logo img {
    width: 60px;
    height: auto;
    animation: bounce 2s infinite;
}


@keyframes bounce {

    0%,
    100% {
        transform: translateY(0);
    }

    50% {
        transform: translateY(-10px);
    }
}

.app-header h1 {
    font-size: 1.8rem;
    font-weight: bold;
    margin: 0;
}


@media (max-width: 600px) {
    .app-header h1 {
        font-size: 1.5rem;
    }

    .app-header .logo img {
        width: 50px;
    }
}
</style>
