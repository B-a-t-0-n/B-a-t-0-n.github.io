<script setup>
import { onBeforeUnmount, onMounted, ref } from 'vue'

const isMenuOpen = ref(false)
const currentYear = new Date().getFullYear()

const navLinks = [
  { label: 'Обо мне', href: '#about' },
  { label: 'Стек', href: '#stack' },
  { label: 'Подход', href: '#approach' },
]

const workflow = [
  { title: 'Требования', note: 'Цели и ограничения' },
  { title: 'Архитектура', note: 'Границы и взаимодействия' },
  { title: 'Реализация', note: 'Frontend и backend' },
  { title: 'Тесты', note: 'Качество и предсказуемость' },
  { title: 'Деплой', note: 'Запуск и наблюдаемость' },
]

const principles = [
  {
    number: '01',
    title: 'Продуктовое мышление',
    text: 'Сначала понимаю задачу, ценность для пользователя и ограничения — потом выбираю технологии.',
  },
  {
    number: '02',
    title: 'Архитектура до кода',
    text: 'Выстраиваю доменные границы, потоки данных и контракты, чтобы систему было легко развивать.',
  },
  {
    number: '03',
    title: 'Полный цикл',
    text: 'Связываю интерфейс, API, данные, тесты и инфраструктуру в один целостный продукт.',
  },
]

const stackGroups = [
  {
    index: '01',
    title: 'Frontend',
    text: 'Быстрые и понятные интерфейсы',
    items: ['Vue 3', 'TypeScript', 'JavaScript', 'Node.js', 'Tailwind CSS', 'Vite', 'HTML5', 'CSS3'],
  },
  {
    index: '02',
    title: 'Backend',
    text: 'Надёжные API и бизнес-логика',
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
    text: 'Ясные границы и управляемая сложность',
    items: ['DDD', 'Clean Architecture', 'Микросервисы', 'Модульный монолит'],
  },
  {
    index: '05',
    title: 'DevOps & Observability',
    text: 'Воспроизводимый запуск и понимание системы',
    items: ['Docker', 'Kubernetes', 'Grafana', 'Loki', 'Alloy', 'OpenTelemetry'],
  },
  {
    index: '06',
    title: 'AI & Agentic Development',
    text: 'Инструменты для усиления и автоматизации разработки',
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
    text: 'Создаю frontend и backend как единую систему: от UI-состояний до API, хранения и интеграций.',
  },
  {
    number: '04',
    title: 'Тестирование',
    text: 'Проверяю основные сценарии, граничные случаи и контракты между частями системы.',
  },
  {
    number: '05',
    title: 'Деплой и наблюдаемость',
    text: 'Контейнеризирую сервисы, выстраиваю релиз и телеметрию, чтобы видеть поведение продукта.',
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
          <span class="brand-mark">VK</span>
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

        <div class="container hero-grid">
          <div class="hero-copy">
            <p class="eyebrow"><span></span> FULLSTACK · WEB PLATFORMS · ARCHITECTURE</p>
            <h1>
              Создаю веб-платформы
              <span>от требований до работающего продукта.</span>
            </h1>
            <p class="hero-lead">
              Меня зовут <strong>Владислав Книгин</strong>. Я fullstack-разработчик: связываю Vue-интерфейсы,
              backend на C# и инфраструктуру в целостные системы.
            </p>

            <div class="hero-actions">
              <a class="button button-primary" href="#stack">
                Изучить стек
                <span aria-hidden="true">↓</span>
              </a>
              <a class="button button-secondary" href="#approach">Как я работаю</a>
            </div>

            <div class="hero-signals" aria-label="Ключевые направления">
              <span>Vue 3</span>
              <span>ASP.NET Core</span>
              <span>DDD</span>
              <span>Kubernetes</span>
            </div>
          </div>

          <aside class="workflow-card" aria-label="Цикл разработки">
            <div class="workflow-header">
              <div class="window-dots" aria-hidden="true"><span></span><span></span><span></span></div>
              <code>fullstack.workflow</code>
              <span class="workflow-status">active</span>
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
              <span><i></i> full_cycle</span>
              <code>status: ready</code>
            </div>
          </aside>
        </div>
      </section>

      <section id="about" class="section about-section">
        <div class="container">
          <div class="section-heading reveal">
            <p class="section-label">01 · Обо мне</p>
            <h2>Разрабатываю не отдельные экраны, а <span>целостные системы.</span></h2>
            <p>
              Активно участвую в создании платформ полного цикла: от анализа задачи и выбора архитектуры до
              реализации, тестов, деплоя и наблюдаемости.
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

      <section id="stack" class="section stack-section">
        <div class="container">
          <div class="section-heading section-heading-row reveal">
            <div>
              <p class="section-label">02 · Технологии</p>
              <h2>Стек, который закрывает <span>весь путь продукта.</span></h2>
            </div>
            <p>От браузера до кластера, от доменной модели до телеметрии.</p>
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

      <section id="approach" class="section approach-section">
        <div class="container approach-layout">
          <div class="approach-intro reveal">
            <p class="section-label">03 · Подход</p>
            <h2>От неопределённости к <span>управляемой системе.</span></h2>
            <p>
              Каждый этап уменьшает риски для следующего: требования направляют архитектуру, архитектура упрощает реализацию, а тесты делают релиз предсказуемым.
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

      <section class="section closing-section">
        <div class="container">
          <div class="closing-card reveal">
            <p class="section-label">FULL CYCLE DEVELOPMENT</p>
            <h2>Сильный продукт — это не набор технологий, а <span>связная система.</span></h2>
            <p>Выбираю инструменты под задачу и довожу решение до работы в реальной среде.</p>
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
          <span class="brand-mark">VK</span>
          <p>Владислав Книгин · Fullstack Developer</p>
        </div>
        <p>© {{ currentYear }} · Сделано на Vue 3</p>
      </div>
    </footer>
  </div>
</template>
