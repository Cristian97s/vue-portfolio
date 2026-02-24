<script setup>
</script>

<template>
    <section class="skills">
        <div class="container">
            <h2 class="section-title">Mi Arsenal Técnico</h2>
            <p class="section-subtitle">Herramientas que utilizo para construir experiencias digitales detalladas y
                escalables.</p>

            <div class="skills-grid">
                <div class="skill-card">
                    <h3>Frontend</h3>
                    <div class="skill-tags">
                        <span>JavaScript</span>
                        <span>React</span>
                        <span>Vue</span>
                    </div>
                </div>

                <div class="skill-card">
                    <h3>Backend</h3>
                    <div class="skill-tags">
                        <span>Python</span>
                        <span>Django</span>
                        <span>FastAPI</span>
                        <span>C# / .NET</span>
                    </div>
                </div>

                <div class="skill-card">
                    <h3>Bases de Datos</h3>
                    <div class="skill-tags">
                        <span>PostgreSQL</span>
                        <span>SQL Server</span>
                        <span>MySQL</span>
                        <span>SQL</span>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<style scoped>
.skills{
    padding: 60px 20px;
    font-family: 'Segoe UI', sans-serif;
    background-color: #0E0F1C;
}

.section-title {
    font-size: 2rem;
    margin-bottom: 10px;
    color: #E7E7E7;
}

.section-subtitle {
    margin-bottom: 40px;
    color: #8892b0;
}

.skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 20px;
}

.skill-card {
    background: #112240;
    padding: 25px;
    border-radius: 12px;
    transition: transform 0.3s ease;
    border: 1px solid rgba(100, 255, 218, 0.1);
}

.skill-card:hover {
    transform: translateY(-5px);
    border-color: #E7E7E7;
}

.skill-card h3 {
    margin-top: 0;
    font-size: 1.2rem;
    margin-bottom: 15px;
}

.skill-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
}

.skill-tags span {
    background: rgba(100, 255, 218, 0.1);
    color: #E7E7E7;
    padding: 5px 12px;
    border-radius: 20px;
    font-size: 0.9rem;
    font-weight: 500;
}
</style>