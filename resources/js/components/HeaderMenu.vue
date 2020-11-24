<template>
  <div>
    <div class="border-b">
      <div class="nav container">
        <div class="brand">
          <object type="image/svg+xml" data="/images/bertazzoni-logo.svg" height="14" width="auto" style="pointer-events: none;">
            <img src="/images/bertazzoni-logo.svg" width="auto" height="14" />
          </object>
        </div>
        <button class="navbar-toggler" type="button" @click.stop="toggleMobileMenu">
          <object type="image/svg+xml" data="/images/grip-lines.svg" height="14" width="auto" style="pointer-events: none;">
            <img src="images/grip-lines.svg" width="auto" height="14">
          </object>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav mx-auto">
            <li class="nav-item active">
              <a class="nav-link" href="#" @click.stop.prevent="toggleProductMenu">Products</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">Service</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">Retailers</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">Our Story</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">Warranties</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">Contact</a>
            </li>
          </ul>
          <form class="form-inline my-2 my-lg-0">
            <img src="/images/search-icon.svg" width="auto" height="15" @click="toggleSearchForm" class="cursor-pointer" />
            <button class="btn">LOG IN</button>
          </form>
          <div v-show="showingSearchForm" class="search">
            <div class="grid grid-cols-12 gap-2">
              <div class="col-span-2">
                <button @click.stop="showCategoryDropdown" class="categories-btn">
                  {{ selectedCategory }}
                  <img src="/images/form-dropdown-arrow.svg" width="auto" height="4" />
                </button>
                <div v-show="showingCategoryDropdown" v-click-outside="hideCategoryDropdown" class="category-dropdown">
                    <div class="category-list" @click="selectCategory('All Categories')">All Categories</div>
                    <div class="category-list" @click="selectCategory('90cm Freestanding')">90cm Freestanding</div>
                    <div class="category-list" @click="selectCategory('120cm Freestanding')">120cm Freestanding</div>
                    <div class="category-list" @click="selectCategory('Double Oven')">Double Oven</div>
                    <div class="category-list" @click="selectCategory('Single Oven')">Single Oven</div>
                    <div class="category-list" @click="selectCategory('Gas Hob')">Gas Hob</div>
                    <div class="category-list" @click="selectCategory('Induction Hob')">Induction Hob</div>
                </div>
              </div>
              <div class="col-span-8">
                <input type="text" ref="searchInput" placeholder="Search keyword or product number">
              </div>
              <div class="col-span-2 flex">
                <button class="search-btn">
                  Search
                </button>
                <img src="/images/close-search.svg" width="auto" height="15" class="close" @click="toggleSearchForm" />
              </div>
            </div> 
          </div>
        </div>
      </div>
      <expandable>
        <div v-show="showingMobileMenu" class="nav-mobile expandable" v-click-outside="hideMobileMenu">
          <div class="menu-row" @click.stop="toggleProductMenu"><h3>Products <img src="/images/menu-arrow.svg" width="auto" height="10" /></h3></div>
          <div class="menu-row"><h3>Service <img src="/images/menu-arrow.svg" width="auto" height="10" /></h3></div>
          <div class="menu-row"><h3>Retailers <img src="/images/menu-arrow.svg" width="auto" height="10" /></h3></div>
          <div class="menu-row"><h3>Our Story <img src="/images/menu-arrow.svg" width="auto" height="10" /></h3></div>
          <div class="menu-row"><h3>Warranties <img src="/images/menu-arrow.svg" width="auto" height="10" /></h3></div>
          <div class="menu-row"><h3>Contact <img src="/images/menu-arrow.svg" width="auto" height="10" /></h3></div>
          <div class="menu-row"><h3>Search <img src="/images/menu-arrow.svg" width="auto" height="10" /></h3></div>
          <div class="menu-row"><h3>Login <img src="/images/menu-arrow.svg" width="auto" height="10" /></h3></div>
        </div>
      </expandable>
    </div>
    <div v-show="showingProductMenu" v-click-outside="hideProductMenu" class="container">
      <div class="menu">
        <div>
          <button>
            All products
          </button>
        </div>
        <div class="grid grid-cols-4 gap-8">
          <div>
            <div class="menu-row">
              <h3>90cm Freestanding Ranges
                <object type="image/svg+xml" data="/images/menu-arrow.svg" height="10" width="auto" style="pointer-events: none;" class="ml-2">
                  <img src="images/menu-arrow.svg" width="auto" height="10" class="ml-2">
                </object>
              </h3>
            </div>
            <div class="menu-row">
              <h3>Gas Hob Ranges
                <object type="image/svg+xml" data="/images/menu-arrow.svg" height="10" width="auto" style="pointer-events: none;" class="ml-2">
                  <img src="images/menu-arrow.svg" width="auto" height="10" class="ml-2">
                </object>
              </h3>
            </div>
          </div>
          <div>
            <div class="menu-row">
              <h3>120cm Freestanding Ranges
                <object type="image/svg+xml" data="/images/menu-arrow.svg" height="10" width="auto" style="pointer-events: none;" class="ml-2">
                  <img src="images/menu-arrow.svg" width="auto" height="10" class="ml-2">
                </object>
              </h3>
            </div>
            <div class="menu-row">
              <h3>Induction Hob Ranges
                <object type="image/svg+xml" data="/images/menu-arrow.svg" height="10" width="auto" style="pointer-events: none;" class="ml-2">
                  <img src="images/menu-arrow.svg" width="auto" height="10" class="ml-2">
                </object>
              </h3>
            </div>
          </div>
          <div>
            <div class="menu-row">
              <h3>Double Oven Ranges
                <object type="image/svg+xml" data="/images/menu-arrow.svg" height="10" width="auto" style="pointer-events: none;" class="ml-2">
                  <img src="images/menu-arrow.svg" width="auto" height="10" class="ml-2">
                </object>
              </h3>
            </div>
          </div>
          <div>
            <div class="menu-row">
              <h3>Single Oven Ranges
                <object type="image/svg+xml" data="/images/menu-arrow.svg" height="10" width="auto" style="pointer-events: none;" class="ml-2">
                  <img src="images/menu-arrow.svg" width="auto" height="10" class="ml-2">
                </object>
              </h3>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      showingProductMenu: false,
      showingSearchForm: false,
      showingCategoryDropdown: false,
      selectedCategory: 'All Categories',
      showingMobileMenu: false,
    }
  },

  watch: {
    showingSearchForm (newValue) {
      if (newValue) {
        this.$nextTick(() => this.$refs.searchInput.focus())
      }
    }
  },

  methods: {
    toggleProductMenu () {
      this.showingProductMenu = ! this.showingProductMenu
    },

    hideProductMenu () {
      this.showingProductMenu = false
    },
    
    toggleSearchForm () {
      this.showingSearchForm = ! this.showingSearchForm
    },

    showCategoryDropdown () {
      this.showingCategoryDropdown = true
    },

    hideCategoryDropdown () {
      this.showingCategoryDropdown = false
    },

    toggleMobileMenu () {
      this.showingMobileMenu = ! this.showingMobileMenu
      this.showingProductMenu = false
    },

    hideMobileMenu () {
      this.showingMobileMenu = false
    },

    selectCategory (category) {
      this.selectedCategory = category
      this.hideCategoryDropdown()
    },
  },
}
</script>
