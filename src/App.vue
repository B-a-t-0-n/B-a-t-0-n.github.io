<script setup>
import { onBeforeUnmount, onMounted, ref } from 'vue'

const isMenuOpen = ref(false)
const currentYear = new Date().getFullYear()

const navLinks = [
  { label: 'Обо мне', href: '#about' },
  { label: 'Подход', href: '#approach' },
  { label: 'Стек', href: '#stack' },
]

const workflow = [
  { title: 'Роль', note: 'Fullstack-разработчик' },
  { title: 'Frontend', note: 'Vue 3 · TypeScript · Vite' },
  { title: 'Backend', note: 'C# · ASP.NET Core · PostgreSQL' },
  { title: 'Архитектура', note: 'DDD · Clean Architecture' },
  { title: 'Инфраструктура', note: 'Docker · Kubernetes · Observability' },
]

const principles = [
  {
    number: '01',
    title: 'Fullstack-разработка',
    text: 'Разрабатываю интерфейс, API, бизнес-логику и работу с данными как части одного веб-приложения.',
  },
  {
    number: '02',
    title: 'Архитектурный подход',
    text: 'Применяю DDD и Clean Architecture. Использую модульный монолит или микросервисы в зависимости от задачи.',
  },
  {
    number: '03',
    title: 'Доставка и эксплуатация',
    text: 'Проверяю ключевые сценарии, контейнеризирую сервисы и настраиваю наблюдаемость после деплоя.',
  },
]

const stackGroups = [
  {
    index: '01',
    title: 'Frontend',
    text: 'Интерфейсы и клиентская логика',
    items: ['Vue 3', 'TypeScript', 'JavaScript', 'Node.js', 'Tailwind CSS', 'Vite', 'HTML5', 'CSS3'],
  },
  {
    index: '02',
    title: 'Backend',
    text: 'API, бизнес-логика и real-time',
    items: ['C#', '.NET', 'ASP.NET Core', 'EF Core', 'Dapper', 'REST API', 'WebSockets'],
  },
  {
    index: '03',
    title: 'Данные и интеграции',
    text: 'Хранение, кэш, сообщения и файлы',
    items: ['PostgreSQL', 'Redis', 'RabbitMQ', 'S3'],
  },
  {
    index: '04',
    title: 'Архитектура',
    text: 'Структура приложения и границы модулей',
    items: ['DDD', 'Clean Architecture', 'Микросервисы', 'Модульный монолит'],
  },
  {
    index: '05',
    title: 'DevOps & Observability',
    text: 'Контейнеризация, оркестрация и телеметрия',
    items: ['Docker', 'Kubernetes', 'Grafana', 'Loki', 'Alloy', 'OpenTelemetry'],
  },
  {
    index: '06',
    title: 'AI & Agentic Development',
    text: 'Agentic-инструменты в процессе разработки',
    items: ['OpenAI Codex', 'AI Agents', 'Skills', 'MCP', 'Hooks', 'Plugins', 'Agent Harness'],
  },
]

const approachSteps = [
  {
    number: '01',
    title: 'Анализ требований',
    text: 'Уточняю бизнес-цели, сценарии, риски и технические ограничения.',
  },
  {
    number: '02',
    title: 'Проектирование архитектуры',
    text: 'Определяю домены, модули, контракты, схему данных и принципы взаимодействия.',
  },
  {
    number: '03',
    title: 'Реализация',
    text: 'Реализую frontend и backend: от UI-состояний до API, хранения данных и интеграций.',
  },
  {
    number: '04',
    title: 'Тестирование',
    text: 'Проверяю основные сценарии, граничные случаи и контракты между частями системы.',
  },
  {
    number: '05',
    title: 'Деплой и наблюдаемость',
    text: 'Контейнеризирую сервисы, настраиваю процесс релиза и телеметрию работающей системы.',
  },
]

let observer

onMounted(() => {
  observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add('is-visible')
          observer.unobserve(entry.target)
        }
      })
    },
    { threshold: 0.12 },
  )

  document.querySelectorAll('.reveal').forEach((element) => observer.observe(element))
})

onBeforeUnmount(() => observer?.disconnect())

function closeMenu() {
  isMenuOpen.value = false
}
</script>

<template>
  <div class="site-shell">
    <a class="skip-link" href="#main-content">К содержанию</a>

    <header class="site-header">
      <div class="container nav-wrap">
        <a class="brand" href="#top" aria-label="Наверх" @click="closeMenu">
          <span class="brand-mark" aria-hidden="true">🥖</span>
          <span class="brand-name">Владислав Книгин</span>
        </a>

        <button
          class="menu-button"
          type="button"
          :aria-expanded="isMenuOpen"
          aria-controls="main-navigation"
          aria-label="Открыть меню"
          @click="isMenuOpen = !isMenuOpen"
        >
          <span></span>
          <span></span>
        </button>

        <nav id="main-navigation" class="main-nav" :class="{ 'is-open': isMenuOpen }" aria-label="Основная навигация">
          <a v-for="link in navLinks" :key="link.href" :href="link.href" @click="closeMenu">
            {{ link.label }}
          </a>
          <a class="nav-github" href="https://github.com/B-a-t-0-n" target="_blank" rel="noreferrer">
            GitHub
            <span aria-hidden="true">↗</span>
          </a>
        </nav>
      </div>
    </header>

    <main id="main-content">
      <section id="top" class="hero section">
        <div class="hero-glow hero-glow-one" aria-hidden="true"></div>
        <div class="hero-glow hero-glow-two" aria-hidden="true"></div>
        <span class="hero-sticker hero-sticker-code" aria-hidden="true">&lt;/&gt;</span>
        <span class="hero-sticker hero-sticker-spark" aria-hidden="true">✶</span>
        <span class="hero-sticker hero-sticker-arrow" aria-hidden="true">↗</span>

        <div class="container hero-grid">
          <div class="hero-copy">
            <p class="eyebrow"><span></span> VUE 3 · C# · ASP.NET CORE</p>
            <h1>
              Владислав Книгин
              <span>Fullstack-разработчик</span>
            </h1>
            <p class="hero-lead">
              Разрабатываю веб-приложения на <strong>Vue 3</strong> и <strong>C# / ASP.NET Core</strong>. Работаю с
              frontend, backend, данными, архитектурой и инфраструктурой — от требований до деплоя и наблюдаемости.
            </p>

            <div class="hero-actions">
              <a class="button button-primary" href="#approach">
                Мой подход
                <span aria-hidden="true">↓</span>
              </a>
              <a class="button button-secondary" href="#stack">Навыки и стек</a>
            </div>

            <div class="hero-signals" aria-label="Ключевые направления">
              <span>Frontend + Backend</span>
              <span>Архитектура</span>
              <span>Тестирование</span>
              <span>Деплой</span>
            </div>
          </div>

          <aside class="workflow-card" aria-label="Краткий профиль разработчика">
            <div class="workflow-header">
              <div class="window-dots" aria-hidden="true"><span></span><span></span><span></span></div>
              <code>developer.profile</code>
              <span class="workflow-status">fullstack</span>
            </div>

            <ol class="workflow-list">
              <li v-for="(step, index) in workflow" :key="step.title">
                <span class="workflow-number">0{{ index + 1 }}</span>
                <span class="workflow-line" aria-hidden="true"></span>
                <span class="workflow-content">
                  <strong>{{ step.title }}</strong>
                  <small>{{ step.note }}</small>
                </span>
              </li>
            </ol>

            <div class="workflow-footer">
              <span><i></i> web_platforms</span>
              <code>vue + .net</code>
            </div>
          </aside>
        </div>
      </section>

      <section id="about" class="section about-section">
        <div class="container">
          <div class="section-heading reveal">
            <p class="section-label">01 · Кто я</p>
            <h2>Fullstack-разработчик, работающий <span>на всех уровнях веб-приложения.</span></h2>
            <p>
              Меня зовут Владислав Книгин. Моя основная специализация — frontend на Vue 3 и backend на C# / ASP.NET
              Core. Помимо реализации, занимаюсь архитектурой, интеграциями, тестированием, контейнеризацией и
              наблюдаемостью.
            </p>
          </div>

          <div class="principles-grid">
            <article v-for="principle in principles" :key="principle.number" class="principle-card reveal">
              <span>{{ principle.number }}</span>
              <h3>{{ principle.title }}</h3>
              <p>{{ principle.text }}</p>
            </article>
          </div>
        </div>
      </section>

      <section id="approach" class="section approach-section">
        <div class="container approach-layout">
          <div class="approach-intro reveal">
            <p class="section-label">02 · Подход</p>
            <h2>Подходы, которых я <span>придерживаюсь в разработке.</span></h2>
            <p>
              Сначала уточняю требования и проектирую архитектуру, затем реализую frontend и backend, проверяю
              основные сценарии и подготавливаю систему к деплою.
            </p>
          </div>

          <ol class="approach-list">
            <li v-for="step in approachSteps" :key="step.number" class="approach-item reveal">
              <span class="approach-number">{{ step.number }}</span>
              <div>
                <h3>{{ step.title }}</h3>
                <p>{{ step.text }}</p>
              </div>
              <span class="approach-arrow" aria-hidden="true">↘</span>
            </li>
          </ol>
        </div>
      </section>

      <section id="stack" class="section stack-section">
        <div class="container">
          <div class="section-heading section-heading-row reveal">
            <div>
              <p class="section-label">03 · Навыки и стек</p>
              <h2>Технологии, с которыми <span>я работаю.</span></h2>
            </div>
            <p>Frontend, backend, данные, архитектура, инфраструктура и agentic AI.</p>
          </div>

          <div class="stack-grid">
            <article v-for="group in stackGroups" :key="group.index" class="stack-card reveal">
              <div class="stack-card-head">
                <span>{{ group.index }}</span>
                <div>
                  <h3>{{ group.title }}</h3>
                  <p>{{ group.text }}</p>
                </div>
              </div>
              <ul>
                <li v-for="item in group.items" :key="item">{{ item }}</li>
              </ul>
            </article>
          </div>
        </div>
      </section>

      <section class="section closing-section">
        <div class="container">
          <div class="closing-card reveal">
            <p class="section-label">КРАТКО</p>
            <h2>Владислав Книгин · <span>Fullstack-разработчик</span></h2>
            <p>
              Vue 3 на frontend, C# и ASP.NET Core на backend, DDD и Clean Architecture, PostgreSQL, Redis,
              RabbitMQ, Docker, Kubernetes и observability.
            </p>
            <a class="button button-light" href="https://github.com/B-a-t-0-n" target="_blank" rel="noreferrer">
              GitHub-профиль
              <span aria-hidden="true">↗</span>
            </a>
          </div>
        </div>
      </section>
    </main>

    <footer class="site-footer">
      <div class="container">
        <div>
          <span class="brand-mark" aria-hidden="true">🥖</span>
          <p>Владислав Книгин · Fullstack Developer</p>
        </div>
        <p>© {{ currentYear }} · Сделано на Vue 3</p>
      </div>
    </footer>
  </div>
</template>
