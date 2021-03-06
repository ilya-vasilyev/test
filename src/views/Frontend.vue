<template>
  <main>
    <p>
      Hello, I'm
      <span>Ilya</span>
      <span>Vasilyev</span> –
      <b>frontend developer</b>,
      specialized in Vue.js, visualization, animation and interactivity, with entrepreneurial experience and

      <!-- eslint-disable -->
      <router-link
        :to="{ name: 'motion' }"
        @click.native="scrollTop()"
      >motion design</router-link>
      skills. Also a
      <router-link
        :to="{ name: 'minimalism' }"
        @click.native="scrollTop()"
      >minimalist</router-link>.
      <!-- eslint-enable -->
    </p>

    <div class="ava">
      <img
        src="/assets/ava.jpg"
        alt="Ilya Vasilyev photo"
      >
    </div>

    <div class="light-header">
      Open CV:
      <!-- eslint-disable -->
      <router-link
        to="/cv"
        @click.native="scrollTop()"
      >html</router-link>
      or
      <a href="/assets/Ilya_Vasilyev_CV.pdf">pdf</a>
      <!-- eslint-enable -->
    </div>

    <p>
      And this is my personal portfolio website, stuffed to the gills with highly annoying, CPU intensive and absolutely unnecessary visual effects.
      I've created them just because I can.
      And you can
      <button
        class="inline"
        @click="toggleEffects()"
      >
        turn them {{ $store.state.showEffects ? 'OFF' : 'ON' }}
      </button>
      anytime.
      <b>This whole project exists only to demonstrate my skills and abilities in web development.</b>
      Here you would know almost everything about me – I can't see any other reasons how you ended up on this page and why you're reading this.
      If you want to dig deeper see
      <a
        href="https://github.com/ilya-vasilyev/iv_portfolio"
        target="_blank"
        rel="noreferrer"
      >source code on Github</a>.
    </p>

    <h2>Profile</h2>
    <p>
      I've been around web development since <b>2013</b>,
      starting from <b>UI</b> and <b>UX</b> design, within startup environment,
      prototyping apps with <b>HTML</b> and <b>CSS</b>, exploring ideas of interactive comics and books,
      transforming these ideas into <b>interactive infographics</b> for the web.
    </p>

    <p>
      Which resulted in a startup about <b>dynamic visualizations of financial models</b>,
      where from the tech side <b>Javascript</b> was inevitable, alongside with <b>D3</b>, <b>GSAP</b>, <b>AngularJS</b> and <b>Node.js</b>,
      and from the founder side: <b>fin analysis</b>, <b>Lean Startup</b>,
      <b>Business Model Canvas</b>, <b>Agile</b>, <b>digital marketing,</b> and <b>sales</b> were learned to keep it going
      for 2 years in searching for a product-market-fit, which was never found.
    </p>
    <p>
      Then there was a series of freelance and consulting projects,
      I've discovered and started learning <b>Vue.js</b>, which is the best frontend framework so far,
      and eventually, I landed on a frontend dev job at the oldest state-independent media in Russia – <b>«Ведомости»</b>.
      That was quite intense, with <b>micro-services</b>, <b>CI/CD</b>,
      migration to <b>Vue with SSR</b> and never-ending backlog.
    </p>
    <p>
      As for now, I want to dive deeper in <b>JAMstack</b>, <b>client-side machine learning</b>,
      <b>graph databases</b> and generally improve my inconsistent knowledge of computer science.
      At the same time, I'm fascinated by the fact that today management is broken,
      so I investigate the areas of <b>DDD</b>, <b>Agile scaling</b>, <b>PMO</b>, <b>The OS Canvas</b>,
      trying to find the right way to reduce stress and increase productivity in the modern workplace.
    </p>
    <img
      v-show="tldrImage"
      ref="tldr-image"
      alt="Peter Griffin peacock"
      class="tldr-image"
    >
    <div>
      <button
        v-if="!tldrImage"
        class="prime"
        @click="toggleTldr()"
      >
        TL;DR
      </button>
    </div>

    <hr>

    <h2>Skills</h2>
    <p>
      You're probably interested <i>(why shouldn't you be?)</i> in my skills end experience in web development.
      Fortunately, I've made a visualization for you.
    </p>
    <small>NOTE: all data is purely subjective and only represents my attitude.</small>
    <p>
      In case you're too lazy to appreciate my data visualization efforts, here is the point:
      <br>
      I really like <b>Vue</b>, I dislike <b>AngularJS</b>, and I disregard <b>React</b>.
      I'm really into <b>frontend</b>, but sometimes I can a little <b>Node</b> or <b>Python</b> if necessary.
    </p>

    <div class="light-header">
      View as:
    </div>
    <div class="skill-controls">
      <button
        :active="viewMode === 'chart'"
        class="prime"
        @click="loadSkillComponent('chart')"
      >
        <b>CHART</b>
      </button>
      <button
        :active="viewMode === 'table'"
        class="prime"
        @click="loadSkillComponent('table')"
      >
        <b>TABLE</b>
      </button>
      <button
        :active="viewMode === 'raw'"
        class="prime"
        @click="loadSkillComponent('raw')"
      >
        <b>JSON</b>
      </button>
    </div>

    <div class="skills-container">
      <div v-if="showSkillsContainer">
        <Chart
          v-if="isSkillComponentLoaded.chart"
          v-show="viewMode === 'chart'"
          class="skills"
        />

        <Table
          v-if="isSkillComponentLoaded.table"
          v-show="viewMode === 'table'"
          class="skills"
        />

        <Raw
          v-if="isSkillComponentLoaded.raw"
          v-show="viewMode === 'raw'"
          class="skills"
        />
        <noscript>
          Can't show with JavaScript turned off
        </noscript>
      </div>
    </div>

    <hr>

    <h2>Experience</h2>
    <p>
      My whole life is the game of opposites:
      <ul class="opposites">
        <li>
          <i>As a kid I was obsessed with 3D modeling and animation because 2D was boring: </i>
          <b>I ended up with the gallery full of drawings on DeviantArt.</b>
        </li>
        <li>
          <i>I joined a college rock-band to play on keys because I was not really interested in all this rock'n'roll stuff: </i>
          <b>I ended up writing, arranging, singing, guitaring, recording and mixing alternative indie rock.</b>
        </li>
        <li>
          <i>On the web I identified myself as a designer, definitely not a coder, because it's not creative enough work: </i>
          <b>as you probably suggested, I ended up as a frontend developer.</b>
        </li>
        <li>
          <i>Once in the office, it was clear to me that I'm the tech guy, having nothing in common with these strange managers: </i>
          <b>guess what I'm interested in right now?</b>
        </li>
      </ul>
    </p>
    <p>
      The following is the illustrated timeline of the most significant activities in recent years.
    </p>
    <small>NOTE: you can scroll timeline horizontally or use arrow buttons below</small>

    <div class="timeline-container">
      <Timeline
        v-if="showTimeline"
        @interaction.once="$ga.event('interaction', 'scroll', 'timeline')"
      />
      <noscript>
        Can't show with JavaScript turned off
      </noscript>
    </div>

    <hr>

    <h2>This site</h2>
    <p>
      <b>Design</b>
      – well, for my projects I usually omit design, jumping from structural pencil sketch right into coding and styling.
      It gives me more flexibility and freedom in making design choices as well as it increases the speed.
    </p>
    <p>
      <b>Vue</b>
      – honestly, I wanted to give Nuxt.js a try for this one,
      but it was so preconfigured and I so much wanted to set up the whole project,
      so I used clean Vue + Vue-router + Vuex, without even Vue-CLI. As you already should know, Vue is my favorite framework.
    </p>
    <p>
      <b>Billboard</b>
      – not almighty yet best that I managed to find declarative chart library on top of the last version of D3.
    </p>
    <p>
      <b>Tabulator</b>
      – a quite powerful lib for tables, with sorting, filtering, and formatting. Now, as they dropped jQuery, I decided to give it a try.
    </p>
    <p>
      <b>Anime</b>
      – so far it works great for lightweight animations, it's small, simple and open-source.
    </p>
    <p>
      <b>CSS grids</b>
      – although I prefer flexbox in most cases, grids are good for complex irregular layouts, so I used them for the portfolio gallery.
    </p>
    <p>
      <b>Browser support</b>
      – tested down to IE11, it mostly works fine, despite using CSS grids and some ES7 features
      <i>(Array.includes, Object.entries)</i>,
      thanks to polyfills and
      <i>@supports()</i> trick.
    </p>
    <p>
      <b>SEO</b>
      – pre-rendering is enough for static sites like this one, and SSR would be overmuch.
      And with microdata, meta tags, proper headers, and content length I hope it would be indexed well enough.
    </p>
    <p>
      <b>Webpack</b>
      – it was the first time I set up Webpack completely from scratch,
      with pre-rendering, a dynamic import of components.
      Works fine but development mode is petty messy,
      you can examine
      <a
        href="./report.html"
        target="_blank"
        rel="noreferrer"
      >Bundle Analyzer report</a>.
    </p>
    <p>
      <b>Netlify</b>
      – just a wonderful way to host static and serverless applications, I use them since their early days.
    </p>
  </main>
</template>

<script>
import LoadingComponent from '@/components/Loading.vue'
import ErrorComponent from '@/components/Error.vue'
import * as tldrGif from '@/assets/images/peacock.gif'

export default {
  name: 'Frontend',
  components: {
    Chart: () => ({
      component: import(/* webpackChunkName: 'chart', webpackPrefetch: true */ '@/components/Chart.vue'),
      loading: LoadingComponent,
      error: ErrorComponent,
      delay: 0,
      timeout: 25000
    }),
    Table: () => ({
      component: import(/* webpackChunkName: 'table', webpackPrefetch: true */ '@/components/Table.vue'),
      loading: LoadingComponent,
      error: ErrorComponent,
      delay: 0,
      timeout: 25000
    }),
    Raw: () => ({
      component: import(/* webpackChunkName: 'raw', webpackPrefetch: true */ '@/components/Raw.vue'),
      loading: LoadingComponent,
      error: ErrorComponent,
      delay: 0,
      timeout: 25000
    }),
    Timeline: () => ({
      component: import(/* webpackChunkName: 'timeline', webpackPrefetch: true */ '@/components/Timeline.vue'),
      loading: LoadingComponent,
      error: ErrorComponent,
      delay: 0,
      timeout: 25000
    })
  },
  data  () {
    return {
      tldrImage: false,
      tldrImageSrc: '',
      viewMode: 'chart',
      isSkillComponentLoaded: { chart: false, table: false, raw: false },
      showSkillsContainer: false,
      showTimeline: false
    }
  },
  mounted () {
    this.loadSkillComponent('chart')
    window.addEventListener('scroll', this.loadSkills)
    window.addEventListener('scroll', this.loadTimeline)
    setTimeout(() => { this.$refs['tldr-image'].src = tldrGif.default }, 4000) // lazy loading
  },
  beforeDestroy () {
    window.removeEventListener('scroll', this.loadSkills)
    window.removeEventListener('scroll', this.loadTimeline)
  },
  methods: {
    hideSkills (callback) {
      this.$anime({
        targets: '.skills',
        translateY: 50,
        opacity: 0,
        filter: this.$store.state.showEffects ? 'blur(5px)' : false,
        duration: 200,
        easing: 'easeInSine',
        complete: callback
      })
    },
    showSkills () {
      this.$anime({
        targets: '.skills',
        translateY: -50,
        duration: 0
      })
      this.$anime({
        targets: '.skills',
        translateY: 0,
        opacity: 1,
        filter: this.$store.state.showEffects ? 'blur(0px)' : false,
        duration: 300,
        easing: 'easeOutBack'
      })
    },
    loadSkillComponent (type) {
      this.hideSkills(() => {
        this.$store.dispatch('loadSkills').then(() => {
          this.isSkillComponentLoaded[type] = true
          this.viewMode = type
          this.showSkills()
        })
      })
    },
    loadSkills (e) {
      let skills = document.querySelector('.skills-container').getBoundingClientRect().top
      if (skills - window.innerHeight < 0) {
        this.showSkillsContainer = true
        window.removeEventListener('scroll', this.loadSkills)
      }
    },
    loadTimeline (e) {
      let timeline = document.querySelector('.timeline-container').getBoundingClientRect().top
      if (timeline - window.innerHeight < 0) {
        this.showTimeline = true
        window.removeEventListener('scroll', this.loadTimeline)
      }
    },
    toggleEffects () {
      this.$store.dispatch('switchEffects', !this.$store.state.showEffects)
        .then(
          this.$ga.event('interaction', 'click', 'effects', this.$store.state.showEffects ? 1 : 0)
        )
    },
    toggleTldr () {
      this.tldrImage = true
      this.$ga.event('interaction', 'click', 'tldr')
    },
    scrollTop () {
      window.scrollTo(0, 0)
    }
  }
}
</script>

<style lang="scss">

$ava-size: 150px;

.ava {
  width: $ava-size;
  height: $ava-size;
  margin: 0 auto;
  position: relative;

  img {
    width: $ava-size;
    height: $ava-size;
    border-radius: $ava-size;
    position: absolute;
    left: 0;
    top: 0;
    z-index: 1;
  }
}

.skill-controls {
  margin: 0 auto 30px;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}

.tldr-image {
  width: 100%;
  max-width: 400px;
  position: relative;
  z-index: 1;
}

.opposites li {
  margin: 15px 0;
}

</style>
