<template>
    <aside class="sidebar" :class="{'sidebar--open' : this.$store.state.sidebarOpen}">
      <nav>
        <ul>
          <li class="section" v-for="{ node } in $static.menu.edges" :key="node.id">
            <h3 class="section-title">{{node.section}}</h3>
            <ul>
              <li v-for="item in node.topics" :key="item.title">
                <g-link class="topic" :to="'/' + item.slug">{{item.title}}</g-link>
              </li>
            </ul>
          </li>
        </ul>
      </nav>
    </aside>
</template>

<static-query>
query Menu {
  menu: allMenu(order:ASC) {
    edges {
      node {
        section
        topics {
          title
          slug
        }
      }
    }
  }
}
</static-query>

<script>

export default {
  watch: {
    '$route' () {
      this.$store.commit('closeSidebar')
    }
  },
  methods: {
    checkAnchors(slug, item) {
      if (slug == item) {
        return true
      }
    },
    stateFromSize: function() {
      if (window.getComputedStyle(document.body, ':before').content == '"small"') {
        this.$store.commit('closeSidebar')
      } else {
        this.$store.commit('openSidebar')
      }
    }
  },
  beforeMount () {
    this.stateFromSize()
  }
}
</script>

<style lang="scss" scoped>
.sidebar {
  transition: background .15s ease-in-out, transform .15s ease-in-out, border-color .15s linear;
  padding: 100px 30px 30px;
  width: 300px;
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  z-index: 9;
  will-change: transform;
  transform: translateX(-300px);
  border-right: 1px solid transparent;
  overflow: auto;

  @include respond-above(sm) {
    transform: translateX(0);
  }

  &--open {
    transform: translateX(0);
  }
  
  .bright & {
    background: $sidebarBright;
    border-color: shade($sidebarBright, 10%);
  }

  .dark & {
    background: $sidebarDark;
    border-color: shade($sidebarDark, 40%);
  }
}

nav {
  position: relative;
  min-height: 100%;
  border: 1px solid transparent;
  padding-bottom: 40px;
}

ul {
  list-style: none;
  padding: 0;
  margin: 0;

  a {
    text-decoration: none;
    color: inherit;
    padding: 5px 0;
    display: block;

    &.active {
      color: $brandPrimary;
    }
  }
}

.section {
  margin-bottom: 30px;
}

.section-title {
  text-transform: uppercase;
  font-size: 12px;
  margin-bottom: 20px;
  opacity: .2;
  letter-spacing: .15em;
}

.topic {
  font-weight: 700;
}

</style>