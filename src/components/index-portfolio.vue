<template>
  <div class="wrapper" id="portfolio">
    <div class="content-wrapper">
      <h2 data-aos="fade">Latest Work</h2>

      <ul>
        <li v-for="(item, index) in portfolio" v-bind:key="index">
          <div class="img-wrapper" data-aos="fade-left">
            <a v-bind:href="item.link">
              <img
                class="hvr hvr-grow"
                v-lazy="require('../assets/img/projects/' + item.img)"
                v-bind:alt="item.title"
              />
            </a>
          </div>

          <div class="text" data-aos="fade-right">
            <h3>
              <a v-bind:href="item.link">{{ item.title }}</a>
            </h3>
            <p>{{ item.description }}</p>
          </div>
        </li>
      </ul>

      <p class="center">
        <router-link class="btn btn-primary" to="/projects"
          >SEE ALL</router-link
        >
      </p>
    </div>
  </div>
</template>

<script>
export default {
  computed: {
    portfolio() {
      return this.$store.getters.portfolio;
    }
  }
};
</script>

<style lang="postcss" scoped>
.wrapper {
  background-color: var(--grey-100);
}

h2,
.text {
  text-align: center;
}

ul {
  display: grid;
  grid-gap: calc(var(--space) * 2);
  list-style-type: none;
  padding-left: 0;
  margin: calc(var(--space) * 2) 0;
}

li {
  display: grid;
  grid-gap: calc(var(--space) * 2);

  & a {
    color: var(--black);
  }

  & img {
    display: block;
    box-shadow: var(--shadow);
    margin: 0 auto;
    max-height: 300px;
  }

  & .text {
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

  & h3 {
    font-size: 2.5rem;
  }

  & p {
    color: var(--grey);
    margin-left: auto;
    margin-right: auto;
    max-width: 40ch;
  }

  @media (--md) {
    grid-template-columns: repeat(2, 1fr);

    &:nth-child(odd) {
      & .img-wrapper {
        order: 1;
      }

      & .text {
        align-items: flex-end;
        text-align: right;
      }

      & p {
        margin-right: 0;
      }
    }

    &:nth-child(even) {
      & .img-wrapper {
        display: flex;
        justify-content: flex-end;
        align-items: flex-start;
      }

      & .text {
        text-align: left;
      }

      & p {
        margin-left: 0;
      }
    }
  }
}

.center {
  margin-left: auto;
  margin-right: auto;
  text-align: center;
}
</style>
