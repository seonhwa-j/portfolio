<script setup lang="ts">
import { computed, onMounted, ref } from "vue";

type Project = {
  title: string;
  period: string;
  client: string;
  company: string;
  role: string;
  platform: string;
  tech: string[];
  featured?: boolean;
};

type Career = {
  company: string;
  period: string;
  position: string;
  task: string;
};

const showArchive = ref(false);

const skills = [
  {
    group: "Markup",
    summary: "표준과 접근성을 고려한 견고한 화면 구조",
    items: ["HTML5", "시멘틱 마크업", "웹표준", "웹접근성", "SEO 구조"],
  },
  {
    group: "Style",
    summary: "유지보수 가능한 스타일 설계와 반응형 레이아웃",
    items: ["CSS3", "SCSS", "반응형 UI", "적응형 레이아웃", "CSS Animation"],
  },
  {
    group: "Script",
    summary: "서비스 맥락에 맞는 UI 인터랙션 구현",
    items: ["JavaScript ES6+", "jQuery", "UI 인터랙션", "레거시 대응"],
  },
  {
    group: "Framework",
    summary: "Vue 중심의 컴포넌트 기반 화면 개발",
    items: ["Vue2", "Vue3", "React", "TypeScript", "Styled-components", "Vuetify", "Element UI"],
  },
  {
    group: "Collaboration",
    summary: "디자인 핸드오프와 운영 환경을 이해한 협업",
    items: ["Git", "Figma", "Zeplin", "디자인 가이드 대응", "운영 유지보수"],
  },
];

const projects: Project[] = [
  {
    title: "케이카 C2C 구축 프로젝트",
    period: "2025.11 - 2026.04",
    client: "케이카",
    company: "엠투엠글로벌",
    role: "C2C 주요 화면 퍼블리싱 및 Vue2/Vue3 기반 UI 컴포넌트 구현",
    platform: "PC Web, Mobile Web, iOS, AOS",
    tech: ["Vue2", "Vue3", "SCSS", "TypeScript", "Element UI"],
    featured: true,
  },
  {
    title: "삼성화재 책무 시스템 리뉴얼",
    period: "2025.06 - 2025.09",
    client: "삼성화재",
    company: "아이티피엠",
    role: "사내 담당책무 모니터링 시스템 화면 개발",
    platform: "Web",
    tech: ["HTML", "CSS", "JavaScript", "넥서스심플"],
    featured: true,
  },
  {
    title: "삼성화재 모니모 앱/웹 리뉴얼",
    period: "2024.02 - 2025.03",
    client: "삼성화재",
    company: "플립",
    role: "모니모와 삼성화재 디자인 가이드 정합성 유지 및 기존 코드 기반 화면 개선",
    platform: "Web, iOS, AOS",
    tech: ["HTML", "SCSS", "Responsive UI"],
    featured: true,
  },
  {
    title: "BMW MyFinCar 2차 구축",
    period: "2021.06 - 2021.11",
    client: "BMW Korea",
    company: "퓨즈",
    role: "대출 및 계약 관련 주요 화면 퍼블리싱",
    platform: "Web, iOS, AOS",
    tech: ["HTML", "CSS", "SCSS", "JavaScript"],
    featured: true,
  },
  {
    title: "KB 개인정보보호 통합관리시스템",
    period: "2022.07 - 2022.10",
    client: "KB 국민은행",
    company: "프로엔",
    role: "사내 개인정보 보호관리 시스템 화면 개발",
    platform: "Web",
    tech: ["Vue2", "Vuetify", "HTML", "CSS", "SCSS", "JavaScript"],
    featured: true,
  },
  {
    title: "KB 마이데이터 통합 분석 플랫폼 구축",
    period: "2022.01 - 2022.02",
    client: "KB 국민은행",
    company: "상원소프트",
    role: "사내 분석 플랫폼 화면 개발",
    platform: "Web",
    tech: ["HTML", "CSS", "SCSS", "JavaScript", "Vue"],
    featured: true,
  },
  {
    title: "파워젠 업무포탈 리뉴얼",
    period: "2023.09 - 2023.11",
    client: "파워젠",
    company: "퓨즈",
    role: "사내 업무포털 화면 개발, 컴포넌트 및 테마 제작",
    platform: "Web",
    tech: ["HTML", "CSS", "React", "Styled-components"],
  },
  {
    title: "하나생명 변액보험 스마트 계약관리 서비스 구축",
    period: "2023.05 - 2023.08",
    client: "하나생명",
    company: "퓨즈",
    role: "계약 가입, 변경, 서비스 안내 등 모바일 화면 개발",
    platform: "iOS, AOS",
    tech: ["HTML", "CSS", "Chart.js", "Responsive UI"],
  },
  {
    title: "허비서 렌트카 플랫폼 개발",
    period: "2022.12 - 2023.03",
    client: "비즈앤플랫폼",
    company: "디자인나인",
    role: "렌트카 대여, 반납, 장기 리스 화면 개발",
    platform: "Web, iOS, AOS",
    tech: ["HTML", "CSS", "Vue"],
  },
  {
    title: "KB DAM 유지보수 및 테마변경",
    period: "2022.04 - 2022.07",
    client: "KB 국민은행",
    company: "프로엔",
    role: "차트 중심 내부 모니터링 서비스 화면 개발 및 테마 변경",
    platform: "Web",
    tech: ["HTML", "CSS", "SCSS", "JavaScript", "Vue"],
  },
  {
    title: "에자이 헬피서비스 리뉴얼",
    period: "2022.02 - 2022.04",
    client: "에자이코리아",
    company: "메디네트웍스",
    role: "건강앱 메인 및 랜딩 화면 퍼블리싱",
    platform: "iOS, AOS",
    tech: ["HTML", "CSS", "SCSS", "JavaScript", "Responsive UI"],
  },
  {
    title: "KT Skylife Home System 리뉴얼",
    period: "2021.11 - 2021.12",
    client: "KT Skylife",
    company: "PD Soft",
    role: "원격 홈 제어 시스템 화면 개발",
    platform: "Web",
    tech: ["HTML", "CSS", "SCSS", "JavaScript", "Vue"],
  },
  {
    title: "SEENARIO 구축",
    period: "2021.10 - 2021.12",
    client: "SEENARIO",
    company: "SEENARIO",
    role: "웹소설, 채팅형 소설 소셜 커뮤니티 화면 개발",
    platform: "iOS, AOS",
    tech: ["HTML", "CSS", "SCSS", "JavaScript"],
  },
  {
    title: "아프리카TV/Apro/샵 운영 및 구축",
    period: "2012.02 - 2020.01",
    client: "아프리카TV",
    company: "아프리카TV",
    role: "HTS 내 웹, 서비스, 이벤트 화면 구축 및 유지보수",
    platform: "Web, iOS, AOS",
    tech: ["HTML", "CSS", "JavaScript"],
  },
  {
    title: "스타벅스 구축 및 유지보수",
    period: "2011.03 - 2011.10",
    client: "스타벅스코리아",
    company: "스타벅스코리아",
    role: "서비스 화면 구축 및 유지보수",
    platform: "Web, iOS, AOS",
    tech: ["HTML", "CSS", "JavaScript"],
  },
];

const careers: Career[] = [
  { company: "엠투엠글로벌", period: "2025.10 - 2026.04", position: "차장", task: "케이카 C2C 서비스 구축" },
  { company: "아이티피엠", period: "2025.06 - 2025.09", position: "프로", task: "삼성화재 책무시스템 리뉴얼" },
  { company: "플립", period: "2024.02 - 2025.03", position: "수석", task: "삼성화재 모니모 리뉴얼" },
  { company: "퓨즈", period: "2023.05 - 2023.11", position: "차장", task: "파워젠 업무포탈, 하나생명 서비스 구축" },
  { company: "프로엔", period: "2022.04 - 2022.10", position: "차장", task: "KB 시스템 리뉴얼 및 유지보수" },
  { company: "아프리카TV", period: "2012.02 - 2020.01", position: "선임", task: "아프리카TV/Apro/샵 구축 및 유지보수" },
  { company: "엘루오C&C", period: "2010.01 - 2012.02", position: "대리", task: "에이전시 프로젝트 구축 및 유지보수" },
];

const featuredProjects = computed(() => projects.filter((project) => project.featured));
const archiveProjects = computed(() => projects.filter((project) => !project.featured));

const scrollToSection = (id: string) => {
  document.getElementById(id)?.scrollIntoView({ behavior: "smooth", block: "start" });
};

onMounted(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add("is-visible");
        }
      });
    },
    { threshold: 0.14 },
  );

  document.querySelectorAll<HTMLElement>("[data-reveal]").forEach((element) => {
    observer.observe(element);
  });
});
</script>

<template>
  <div class="site-shell">
    <header class="site-header" aria-label="주요 메뉴">
      <div class="site-header__inner">
        <a class="brand" href="#top" aria-label="정선화 포트폴리오 홈">
          <span>JSH</span>
        </a>
        <nav class="nav">
          <button type="button" @click="scrollToSection('about')">소개</button>
          <button type="button" @click="scrollToSection('projects')">프로젝트</button>
          <button type="button" @click="scrollToSection('career')">경력</button>
          <button type="button" @click="scrollToSection('contact')">연락처</button>
        </nav>
      </div>
    </header>

    <main id="top">
      <section class="hero section">
        <div class="hero__copy" data-reveal>
          <p class="eyebrow">Web Publisher Portfolio</p>
          <p class="hero__title">15년차 웹퍼블리셔</p>
          <h1>정선화</h1>
          <p class="hero__description">웹표준과 접근성을 기반으로 안정적인 화면 구조를 설계하고, 다양한 서비스 환경에서 오래 유지되는 UI를 구현합니다.</p>
          <div class="hero__actions">
            <button class="button button--primary" type="button" @click="scrollToSection('projects')">대표 프로젝트 보기</button>
            <a class="button button--ghost" href="mailto:lemoncloud@naver.com">메일 보내기</a>
          </div>
        </div>

        <aside class="hero__meta" aria-label="핵심 역량" data-reveal>
          <p class="hero__meta-label">Selected Profile</p>
          <dl>
            <div>
              <dt>Experience</dt>
              <dd>15+ years</dd>
            </div>
            <div>
              <dt>Specialty</dt>
              <dd>Accessible UI, Semantic Markup, Responsive Web</dd>
            </div>
            <div>
              <dt>Core Stack</dt>
              <dd>Vue · SCSS · JavaScript · TypeScript</dd>
            </div>
          </dl>
        </aside>
      </section>

      <section id="about" class="section about" data-reveal>
        <div class="section-heading">
          <p class="eyebrow">About</p>
          <h2>구축과 운영을 모두 이해하는 퍼블리셔</h2>
        </div>
        <div class="about__grid">
          <p>15년 이상 금융, 모빌리티, 커머스, 플랫폼 서비스의 웹/모바일 화면을 구축하고 운영했습니다. 디자인 가이드와 기존 코드 환경을 빠르게 파악해 프로젝트에 맞는 구조로 완성도 높은 UI를 구현하는 데 강점이 있습니다.</p>
          <p>HTML5 기반 시멘틱 마크업, SCSS 구조화, JavaScript 인터랙션, Vue 기반 컴포넌트 구현까지 실무에 필요한 범위를 유연하게 다룹니다. 웹표준, 접근성, 반응형, 크로스브라우징을 기본값으로 두고 유지보수하기 쉬운 화면을 만듭니다.</p>
        </div>
      </section>

      <section class="section skills" aria-labelledby="skills-title">
        <div class="section-heading" data-reveal>
          <p class="eyebrow">Skills</p>
          <h2 id="skills-title">현장에서 바로 쓰이는 기술</h2>
        </div>
        <div class="skills__grid">
          <article v-for="skill in skills" :key="skill.group" class="skill-card" data-reveal>
            <span>{{ skill.group }}</span>
            <h3>{{ skill.summary }}</h3>
            <ul>
              <li v-for="item in skill.items" :key="item">{{ item }}</li>
            </ul>
          </article>
        </div>
      </section>

      <section id="projects" class="section projects" aria-labelledby="projects-title">
        <div class="section-heading section-heading--split" data-reveal>
          <div>
            <p class="eyebrow">Featured Projects</p>
            <h2 id="projects-title">대표 프로젝트</h2>
          </div>
          <p>최근 프로젝트와 브랜드 인지도가 높은 프로젝트를 중심으로 구성했습니다.</p>
        </div>

        <div class="project-grid">
          <article v-for="(project, index) in featuredProjects" :key="project.title" class="project-card" data-reveal>
            <span class="project-card__number">{{ String(index + 1).padStart(2, "0") }}</span>
            <div class="project-card__body">
              <div class="project-card__top">
                <span>{{ project.client }}</span>
                <small>{{ project.period }}</small>
              </div>
              <h3>{{ project.title }}</h3>
              <p>{{ project.role }}</p>
              <dl>
                <div>
                  <dt>Platform</dt>
                  <dd>{{ project.platform }}</dd>
                </div>
                <div>
                  <dt>Company</dt>
                  <dd>{{ project.company }}</dd>
                </div>
              </dl>
              <ul class="tags">
                <li v-for="tech in project.tech" :key="tech">{{ tech }}</li>
              </ul>
            </div>
          </article>
        </div>

        <div class="archive-control" data-reveal>
          <button class="button button--primary" type="button" @click="showArchive = !showArchive">
            {{ showArchive ? "프로젝트 접기" : "나머지 프로젝트 더 보기" }}
          </button>
        </div>

        <div v-if="showArchive" class="archive">
          <div class="archive__scroll" tabindex="0">
            <table>
              <caption>
                기타 프로젝트 목록
              </caption>
              <thead>
                <tr>
                  <th scope="col">프로젝트</th>
                  <th scope="col">기간</th>
                  <th scope="col">고객사</th>
                  <th scope="col">역할</th>
                  <th scope="col">기술</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="project in archiveProjects" :key="project.title">
                  <td>{{ project.title }}</td>
                  <td>{{ project.period }}</td>
                  <td>{{ project.client }}</td>
                  <td>{{ project.role }}</td>
                  <td>{{ project.tech.join(", ") }}</td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </section>

      <section id="career" class="section career" aria-labelledby="career-title">
        <div class="section-heading" data-reveal>
          <p class="eyebrow">Career</p>
          <h2 id="career-title">경력 흐름</h2>
        </div>
        <ol class="timeline">
          <li v-for="career in careers" :key="`${career.company}-${career.period}`" data-reveal>
            <span>{{ career.period }}</span>
            <div>
              <h3>{{ career.task }}</h3>
              <p>{{ career.company }} · {{ career.position }}</p>
            </div>
          </li>
        </ol>
      </section>

      <section id="contact" class="section contact" data-reveal>
        <div>
          <p class="eyebrow">Contact</p>
          <h2>함께 일할 준비가 되어 있습니다.</h2>
          <p>구축, 운영, 리뉴얼 환경에서 빠르게 맥락을 파악하고 안정적인 UI 결과물을 만듭니다.</p>
        </div>
        <address>
          <a href="mailto:lemoncloud@naver.com">lemoncloud@naver.com</a>
          <span>서울시 은평구</span>
        </address>
      </section>
    </main>
  </div>
</template>
