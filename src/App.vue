<script setup>
import { ref, computed } from 'vue'

const mobileMenuOpen = ref(false)

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value
}

const closeMobileMenu = () => {
  mobileMenuOpen.value = false
}

const selectedCategory = ref('Food')

const categories = [
  'Food',
  'Swallow',
  'Soup',
  'Snacks',
  'Protein',
  'Drinks',
  'Side Food'
]

const menu = [
  // FOOD
  { category: 'Food', name: 'Jollof Rice', price: 500, image: '/images/menu/jollof-rice.jpg', description: 'Delicious Nigerian-style jollof rice.' },
  { category: 'Food', name: 'Fried Rice', price: 500, image: '/images/menu/fried-rice.jpg', description: 'Freshly prepared fried rice.' },
  { category: 'Food', name: 'Rice and Beans', price: 500, image: '/images/menu/rice-beans.jpg', description: 'Classic rice and beans served fresh.' },
  { category: 'Food', name: 'Chinese Rice', price: 1200, image: '/images/menu/chinese-rice.jpg', description: 'Flavorful Chinese-style rice.' },
  { category: 'Food', name: 'Native Rice', price: 1200, image: '/images/menu/native-rice.jpg', description: 'Richly seasoned native Nigerian rice.' },
  { category: 'Food', name: 'Oriental Rice', price: 1500, image: '/images/menu/oriental-rice.jpg', description: 'Special oriental-style rice.' },
  { category: 'Food', name: 'Asun Rice', price: 1500, image: '/images/menu/asun-rice.jpg', description: 'Tasty rice with spicy asun flavour.' },
  { category: 'Food', name: 'Coconut Rice', price: 1500, image: '/images/menu/coconut-rice.jpg', description: 'Creamy and delicious coconut rice.' },
  { category: 'Food', name: 'Ofada Rice', price: 3000, image: '/images/menu/ofada-rice.jpg', description: 'Authentic Nigerian Ofada rice.' },
  { category: 'Food', name: 'Spaghetti', price: 500, image: '/images/menu/spaghetti.jpg', description: 'Freshly prepared spaghetti.' },
  { category: 'Food', name: 'Yamarita', price: 1000, image: '/images/menu/yamarita.jpg', description: 'Crispy golden yamarita.' },

  // SWALLOW
  { category: 'Swallow', name: 'Fufu', price: 300, image: '/images/menu/fufu.jpg', description: 'Soft and smooth Nigerian fufu.' },
  { category: 'Swallow', name: 'Garri', price: 500, image: '/images/menu/garri.jpg', description: 'Smooth garri served fresh.' },
  { category: 'Swallow', name: 'Semo', price: 500, image: '/images/menu/semo.jpg', description: 'Soft and smooth semovita.' },
  { category: 'Swallow', name: 'Pounded Yam', price: 700, image: '/images/menu/pounded-yam.jpg', description: 'Smooth traditional pounded yam.' },
  { category: 'Swallow', name: 'Amala', price: 500, image: '/images/menu/amala.jpg', description: 'Authentic Nigerian amala.' },
  { category: 'Swallow', name: 'Agidi', price: 300, image: '/images/menu/Agidi.jpg', description: 'Authentic Nigerian agidi.' },

  // SOUP
  { category: 'Soup', name: 'White Okro', price: 500, image: '/images/menu/white-okro.jpg', description: 'Fresh and tasty white okro soup.' },
  { category: 'Soup', name: 'Egusi', price: 700, image: '/images/menu/egusi.jpg', description: 'Rich Nigerian egusi soup.' },
  { category: 'Soup', name: 'Efo', price: 800, image: '/images/menu/efo.jpg', description: 'Delicious traditional efo soup.' },
  { category: 'Soup', name: 'Vegetable Soup', price: 1000, image: '/images/menu/vegetable-soup.jpg', description: 'Fresh Nigerian vegetable soup.' },
  { category: 'Soup', name: 'Bitter Leaf', price: 1000, image: '/images/menu/bitter-leaf.jpg', description: 'Traditional bitter leaf soup.' },
  { category: 'Soup', name: 'Special Okro', price: 1000, image: '/images/menu/special-okro.jpg', description: 'Specially prepared okro soup.' },

  // SNACKS
  { category: 'Snacks', name: 'Doughnut', price: 500, image: '/images/menu/doughnut.jpg', description: 'Soft freshly made doughnut.' },
  { category: 'Snacks', name: 'Jam Doughnut', price: 800, image: '/images/menu/jam-doughnut.jpg', description: 'Soft doughnut filled with jam.' },
  { category: 'Snacks', name: 'Milky Doughnut', price: 1000, image: '/images/menu/milky-doughnut.jpg', description: 'Creamy milky doughnut.' },
  { category: 'Snacks', name: 'Meatpie', price: 1000, image: '/images/menu/meatpie.jpg', description: 'Golden Nigerian meat pie.' },
  { category: 'Snacks', name: 'Popcorn', price: 1500, image: '/images/menu/popcorn.jpg', description: 'Fresh crunchy popcorn.' },
  { category: 'Snacks', name: 'Medium Bread', price: 1700, image: '/images/menu/medium-bread.jpg', description: 'Freshly baked medium bread.' },
  { category: 'Snacks', name: 'Big Bread', price: 1900, image: '/images/menu/big-bread.jpg', description: 'Freshly baked big bread.' },

  // PROTEIN
  { category: 'Protein', name: 'Egg', price: 500, image: '/images/menu/egg.jpg', description: 'Freshly prepared egg.' },
  { category: 'Protein', name: 'Pomo', price: 700, image: '/images/menu/pomo.jpg', description: 'Well-seasoned Nigerian pomo.' },
  { category: 'Protein', name: 'Intestine', price: 700, image: '/images/menu/intestine.jpg', description: 'Well-prepared spicy intestine.' },
  { category: 'Protein', name: 'Beef', price: 1000, image: '/images/menu/beef.jpg', description: 'Tender seasoned beef.' },
  { category: 'Protein', name: 'Wara', price: 1000, image: '/images/menu/wara.jpg', description: 'Fresh Nigerian wara.' },
  { category: 'Protein', name: 'Goatmeat', price: 2500, image: '/images/menu/goat-meat.jpg', description: 'Tender seasoned goat meat.' },
  { category: 'Protein', name: 'Catfish', price: 2500, image: '/images/menu/catfish.jpg', description: 'Deliciously prepared catfish.' },
  { category: 'Protein', name: 'Medium Titus', price: 1500, image: '/images/menu/medium-titus.jpg', description: 'Medium Titus fish.' },
  { category: 'Protein', name: 'Big Titus', price: 3000, image: '/images/menu/big-titus.jpg', description: 'Large Titus fish.' },
  { category: 'Protein', name: 'Medium Hake Panla', price: 2000, image: '/images/menu/medium-hake.jpg', description: 'Medium hake panla.' },
  { category: 'Protein', name: 'Big Hake Panla', price: 4000, image: '/images/menu/big-hake.jpg', description: 'Large hake panla.' },
  { category: 'Protein', name: 'Chicken', price: 4000, image: '/images/menu/chicken.jpg', description: 'Juicy seasoned chicken.' },
  { category: 'Protein', name: 'Turkey', price: 6000, image: '/images/menu/turkey.jpg', description: 'Tender seasoned turkey.' },

  // DRINKS
  { category: 'Drinks', name: 'Water', price: 300, image: '/images/menu/water.jpg', description: 'Refreshing bottled water.' },
  { category: 'Drinks', name: '7up', price: 400, image: '/images/menu/7up.jpg', description: 'Refreshing chilled 7up.' },
  { category: 'Drinks', name: 'Pepsi', price: 400, image: '/images/menu/pepsi.jpg', description: 'Refreshing chilled Pepsi.' },
  { category: 'Drinks', name: 'Miranda', price: 400, image: '/images/menu/miranda.jpg', description: 'Refreshing Miranda drink.' },
  { category: 'Drinks', name: 'Teem', price: 400, image: '/images/menu/teem.jpg', description: 'Refreshing Teem drink.' },
  { category: 'Drinks', name: 'Small Coke', price: 400, image: '/images/menu/small-coke.jpg', description: 'Chilled Coca-Cola.' },
  { category: 'Drinks', name: 'Medium Fanta', price: 400, image: '/images/menu/medium-fanta.jpg', description: 'Chilled Fanta.' },
  { category: 'Drinks', name: 'Medium Sprite', price: 400, image: '/images/menu/medium-sprite.jpg', description: 'Chilled Sprite.' },
  { category: 'Drinks', name: 'Can Coke', price: 550, image: '/images/menu/can-coke.jpg', description: 'Cold canned Coca-Cola.' },
  { category: 'Drinks', name: 'Can Fanta', price: 550, image: '/images/menu/can-fanta.jpg', description: 'Cold canned Fanta.' },
  { category: 'Drinks', name: 'Can Sprite', price: 550, image: '/images/menu/can-sprite.jpg', description: 'Cold canned Sprite.' },
  { category: 'Drinks', name: '50cl Coke', price: 600, image: '/images/menu/50cl-coke.jpg', description: 'Refreshing 50cl Coca-Cola.' },
  { category: 'Drinks', name: '50cl Fanta', price: 600, image: '/images/menu/50cl-fanta.jpg', description: 'Refreshing 50cl Fanta.' },
  { category: 'Drinks', name: '50cl Sprite', price: 600, image: '/images/menu/50cl-sprite.jpg', description: 'Refreshing 50cl Sprite.' },
  { category: 'Drinks', name: 'Can Schweppes', price: 600, image: '/images/menu/can-schweppes.jpg', description: 'Refreshing Schweppes.' },
  { category: 'Drinks', name: 'Plastic Schweppes', price: 600, image: '/images/menu/plastic-schweppes.jpg', description: 'Refreshing Schweppes.' },
  { category: 'Drinks', name: 'Predator', price: 600, image: '/images/menu/predator.jpg', description: 'Refreshing energy drink.' },
  { category: 'Drinks', name: 'Malt', price: 700, image: '/images/menu/malt.jpg', description: 'Refreshing malt drink.' },
  { category: 'Drinks', name: '50cl Zobo', price: 750, image: '/images/menu/50cl-zobo.jpg', description: 'Fresh Nigerian zobo.' },
  { category: 'Drinks', name: '1 Liter Zobo', price: 1300, image: '/images/menu/1-liter-zobo.jpg', description: 'Fresh 1-liter zobo.' },
  { category: 'Drinks', name: '50cl Orange', price: 1500, image: '/images/menu/50cl-orange.jpg', description: 'Fresh orange drink.' },
  { category: 'Drinks', name: 'Watermelon', price: 1500, image: '/images/menu/watermelon.jpg', description: 'Fresh watermelon drink.' },
  { category: 'Drinks', name: '50cl Pineapple', price: 1500, image: '/images/menu/50cl-pineapple.jpg', description: 'Fresh pineapple drink.' },
  { category: 'Drinks', name: '50cl Tigernut', price: 2000, image: '/images/menu/50cl-tigernut.jpg', description: 'Fresh tigernut drink.' },


  //SIDE FOOD
  { category: 'Side Food', name: 'Plantain', price: 500, image: '/images/menu/plantain.jpg', description: 'Delicious fried plantain.' },
  { category: 'Side Food', name: 'Medium moi-moi', price: 500, image: '/images/menu/medium-moimoi.jpg', description: 'Delicious Nigerian-style moimoi.' },
  { category: 'Side Food', name: 'Big moi-moi', price: 1000, image: '/images/menu/big-moimoi.jpg', description: 'Delicious Nigerian-style moimoi.' },
  { category: 'Side Food', name: 'Salad', price: 500, image: '/images/menu/salad.jpg', description: 'yommy salad.' },

]


const filteredMenu = computed(() =>
  menu.filter(item => item.category === selectedCategory.value)
)

const formatPrice = (price) =>
  new Intl.NumberFormat('en-NG').format(price)

  const order = ref([])

const addToOrder = (item) => {
  const existingItem = order.value.find(
    orderItem => orderItem.name === item.name
  )

  if (existingItem) {
    existingItem.quantity++
  } else {
    order.value.push({
      ...item,
      quantity: 1
    })
  }

  
  setTimeout(() => {
    const orderBox = document.querySelector('.order-box')

    if (orderBox) {
      orderBox.scrollIntoView({
        behavior: 'smooth',
        block: 'center'
      })
    }
  }, 100)
}

const removeFromOrder = (item) => {
  const index = order.value.findIndex(
    orderItem => orderItem.name === item.name
  )

  if (index !== -1) {
    order.value.splice(index, 1)
  }
}

const increaseQuantity = (item) => {
  item.quantity++
}

const decreaseQuantity = (item) => {
  if (item.quantity > 1) {
    item.quantity--
  } else {
    removeFromOrder(item)
  }
}

const orderTotal = computed(() => {
  return order.value.reduce(
    (total, item) => total + item.price * item.quantity,
    0
  )
})

const whatsappOrder = () => {
  if (order.value.length === 0) return

  let message =
    `Hello Farfad Kitchen! 👋\n\n` +
    `I would like to place an order:\n\n`

  order.value.forEach(item => {
    message +=
      `${item.name} x${item.quantity} - ₦${formatPrice(
        item.price * item.quantity
      )}\n`
  })

  message +=
    `\nTotal: ₦${formatPrice(orderTotal.value)}`

  const whatsappUrl =
    `https://wa.me/2347012920913?text=${encodeURIComponent(message)}`

  window.open(whatsappUrl, '_blank')
}
</script>



<template>
  <div class="app">

   <header class="navbar">
  <div class="nav-container">

    <a href="#home" class="logo">
      <img
        src="/images/farfad-logo.png"
        alt="Farfad Kitchen"
      >
    </a>
    

    <nav class="nav-links">
      <a href="#home">Home</a>
      <a href="#menu">Menu</a>
      <a href="#about">About Us</a>
      <a href="#gallery">Gallery</a>
      <a href="#testimonial">Testimonial</a>
      <a href="#contact">Contact</a>
    </nav>

    <div v-if="mobileMenuOpen" class="mobile-menu">
  <a href="#home" @click="closeMobileMenu">Home</a>
  <a href="#menu" @click="closeMobileMenu">Menu</a>
  <a href="#about" @click="closeMobileMenu">About Us</a>
  <a href="#gallery" @click="closeMobileMenu">Gallery</a>
  <a href="#testimonial" @click="closeMobileMenu">Testimonial</a>
  <a href="#contact" @click="closeMobileMenu">Contact</a>

  <a
    href="#menu"
    class="mobile-order-btn"
    @click="closeMobileMenu"
  >
    Order Now
  </a>
</div>

    <a href="#menu" class="nav-order-btn">
      Order Now
    </a>

    <button
  class="menu-toggle"
  aria-label="Open menu"
  @click="toggleMobileMenu"
>
  {{ mobileMenuOpen ? '✕' : '☰' }}
</button>

  </div>
</header>
</div>


    <section id="home" class="hero">
  <div class="hero-overlay"></div>

  <div class="hero-content">
    <div class="hero-badge">
      🍽️ FRESH • TASTY • LOCAL
    </div>

    <h1>
      Taste the Best of
      <span>Naija</span>
    </h1>
    
    <p>
      Delicious Nigerian meals, refreshing drinks and quality service —
      freshly prepared for you at Farfad Kitchen.
    </p>

    <div class="hero-buttons">
      <a href="#menu" class="hero-primary-btn">
        Explore Our Menu
      </a>

      <a href="#contact" class="hero-secondary-btn">
        Visit Us
      </a>
    </div>

    <div class="hero-details">
      <div>
        <strong>🍛</strong>
        <span>Fresh Meals</span>
      </div>

      <div>
        <strong>🥤</strong>
        <span>Fresh Drinks</span>
      </div>

      <div>
        <strong>❤️</strong>
        <span>Made With Care</span>
      </div>
    </div>
  </div>
</section>
    


      <!-- INTRO -->
      <section class="intro">

        <div class="intro-container">

          <div class="intro-text">

            <span class="section-label">
              WELCOME TO FARFAD
            </span>

            <h2>
              Good Food.
              <span>Good Mood.</span>
            </h2>

            <p>
              At Farfad Kitchen, every meal is prepared with passion,
              quality ingredients and a commitment to giving you a taste
              you will always remember.
            </p>

          </div>

          <div class="intro-card">

            <div class="card-icon">
              👨‍🍳
            </div>

            <h3>
              Prepared With Passion
            </h3>

            <p>
              Delicious meals made specially for you.
            </p>

          </div>

          <div class="intro-card green-card">

            <div class="card-icon">
              🍛
            </div>

            <h3>
              Authentic Taste
            </h3>

            <p>
              Enjoy the rich taste of Nigerian cuisine.
            </p>

          </div>

        </div>

      </section>


<section id="menu" class="menu-section">
  <div class="section-heading">
    <p class="section-tag">OUR MENU</p>
    <h2>Something Delicious <span>For Everyone</span></h2>
    <p>
      Freshly prepared meals, delicious proteins, snacks and refreshing drinks.
    </p>
  </div>

  <div class="menu-tabs">
    <button
      v-for="category in categories"
      :key="category"
      class="menu-tab"
      :class="{ active: selectedCategory === category }"
      @click="selectedCategory = category"
    >
      {{ category }}
    </button>
  </div>

  <div class="real-menu-grid">
    <article
      v-for="item in filteredMenu"
      :key="item.name"
      class="real-food-card"
    >
      <div class="real-food-image">
        <img :src="item.image" :alt="item.name">
        <span class="food-category">{{ item.category }}</span>
      </div>

      <div class="real-food-content">
        <h3>{{ item.name }}</h3>

        <p>{{ item.description }}</p>

        <div class="food-bottom">
          <strong>₦{{ formatPrice(item.price) }}</strong>

          <button
  class="add-order-btn"
  @click="addToOrder(item)"
>
  Add to Order
</button>
        </div>
      </div>
    </article>
  </div>
  <div v-if="order.length > 0" class="order-box">

  <div class="order-header">
    <div>
      <p class="section-tag">YOUR ORDER</p>
      <h3>Order Summary</h3>
    </div>

    <strong>{{ order.length }} item(s)</strong>
  </div>

  <div class="order-items">

    <div
      v-for="item in order"
      :key="item.name"
      class="order-item"
    >
      <div class="order-item-info">
        <img :src="item.image" :alt="item.name">

        <div>
          <h4>{{ item.name }}</h4>
          <p>₦{{ formatPrice(item.price) }}</p>
        </div>
      </div>

      <div class="quantity-control">
        <button @click="decreaseQuantity(item)">−</button>
        <span>{{ item.quantity }}</span>
        <button @click="increaseQuantity(item)">+</button>
      </div>

      <strong>
        ₦{{ formatPrice(item.price * item.quantity) }}
      </strong>

      <button
        class="remove-order"
        @click="removeFromOrder(item)"
      >
        ×
      </button>
    </div>

  </div>

  <div class="order-total">
    <span>Total</span>
    <strong>₦{{ formatPrice(orderTotal) }}</strong>
  </div>

  <button class="whatsapp-order-btn" @click="whatsappOrder">
    Order on WhatsApp
  </button>

</div>
</section>



    <section id="about" class="about-section">
  <div class="about-container">

    <div class="about-image">
      <img
        src="/images/farfad-building.png"
        alt="Farfad Kitchen restaurant"
      >

      <div class="about-image-badge">
        <strong>Farfad</strong>
        <span>Kitchen</span>
      </div>
    </div>

    <div class="about-content">
      <p class="section-tag">ABOUT FARFAD KITCHEN</p>

      <h2>
        Good Food.
        <span>Great Taste.</span>
        Happy Moments.
      </h2>

      <p class="about-text">
        At Farfad Kitchen, we believe good food brings people together.
        We prepare delicious meals with care, using quality ingredients
        and flavours inspired by the richness of Nigerian cuisine.
      </p>

      <p class="about-text">
        Whether you're stopping by for a quick meal, enjoying a refreshing
        drink or ordering your favourite dish, we're here to give you a
        satisfying food experience and friendly service.
      </p>

      <div class="about-features">

        <div class="about-feature">
          <div class="about-feature-icon">🍛</div>
          <div>
            <h3>Fresh Meals</h3>
            <p>Delicious meals prepared with care.</p>
          </div>
        </div>

        <div class="about-feature">
          <div class="about-feature-icon">⭐</div>
          <div>
            <h3>Quality Service</h3>
            <p>We care about every customer's experience.</p>
          </div>
        </div>

        <div class="about-feature">
          <div class="about-feature-icon">❤️</div>
          <div>
            <h3>Made With Care</h3>
            <p>Great taste is always our priority.</p>
          </div>
        </div>

        <div class="about-feature">
          <div class="about-feature-icon">📍</div>
          <div>
            <h3>Easy To Find</h3>
            <p>Visit us at FHA Lugbe, Abuja.</p>
          </div>
        </div>

      </div>

      <a href="#menu" class="about-button">
        Explore Our Menu →
      </a>
    </div>

  </div>
</section>


      <section id="gallery" class="gallery-section">
  <div class="gallery-container">

    <div class="section-heading gallery-heading">
      <p class="section-tag">OUR GALLERY</p>

      <h2>
        A Taste of
        <span>Farfad Kitchen</span>
      </h2>

      <p>
        Take a look at our kitchen, meals and the Farfad Kitchen experience.
      </p>
    </div>

    <div class="gallery-grid">

      <div class="gallery-item gallery-large">
        <img
          src="/images/farfad-building.png"
          alt="Farfad Kitchen restaurant"
        >

        <div class="gallery-overlay">
          <span>📍</span>
          <div>
            <strong>Farfad Kitchen</strong>
            <small>FHA Lugbe, Abuja</small>
          </div>
        </div>
      </div>

      <div class="gallery-item">
        <img
          src="/images/menu/jollof-rice.jpg"
          alt="Jollof rice"
        >

        <div class="gallery-overlay">
          <span>🍛</span>
          <div>
            <strong>Delicious Meals</strong>
            <small>Freshly prepared</small>
          </div>
        </div>
      </div>

      <div class="gallery-item">
        <img
          src="/images/menu/fried-rice.jpg"
          alt="Fried rice"
        >

        <div class="gallery-overlay">
          <span>🍚</span>
          <div>
            <strong>Great Taste</strong>
            <small>Made with care</small>
          </div>
        </div>
      </div>

      <div class="gallery-item">
        <img
          src="/images/menu/chicken.jpg"
          alt="Chicken"
        >

        <div class="gallery-overlay">
          <span>🍗</span>
          <div>
            <strong>Quality Protein</strong>
            <small>Perfectly prepared</small>
          </div>
        </div>
      </div>

      <div class="gallery-item">
        <img
          src="/images/menu/egusi.jpg"
          alt="Egusi soup"
        >

        <div class="gallery-overlay">
          <span>🥣</span>
          <div>
            <strong>Nigerian Flavours</strong>
            <small>Rich & delicious</small>
          </div>
        </div>
      </div>

    </div>

    <div class="gallery-button-wrapper">
      <a href="#menu" class="gallery-button">
        Explore Our Menu →
      </a>
    </div>

  </div>
      </section>
    
  <!-- TESTIMONIALS -->
<section id="testimonial" class="testimonial-section">
  <div class="testimonial-container">

    <div class="section-heading testimonial-heading">
      <p class="section-tag">CUSTOMER LOVE</p>

      <h2>
        What Our Customers
        <span>Say</span>
      </h2>

      <p>
        Good food tastes even better when our customers enjoy every bite.
      </p>
    </div>

    <div class="testimonial-grid">

      <article class="testimonial-card">
        <div class="testimonial-stars">
          ★★★★★
        </div>

        <p class="testimonial-text">
          “The food was delicious and freshly prepared.
          I really enjoyed my meal and the service was excellent.”
        </p>

        <div class="testimonial-person">
          <div class="testimonial-avatar">C</div>

          <div>
            <h3>Happy Customer</h3>
            <span>Farfad Kitchen Customer</span>
          </div>
        </div>
      </article>

      <article class="testimonial-card featured-testimonial">
        <div class="testimonial-stars">
          ★★★★★
        </div>

        <p class="testimonial-text">
          “Farfad Kitchen has become one of my favourite places
          to get good Nigerian food in Abuja.”
        </p>

        <div class="testimonial-person">
          <div class="testimonial-avatar">S</div>

          <div>
            <h3>Satisfied Customer</h3>
            <span>Farfad Kitchen Customer</span>
          </div>
        </div>
      </article>

      <article class="testimonial-card">
        <div class="testimonial-stars">
          ★★★★★
        </div>

        <p class="testimonial-text">
          “Great taste, good portions and friendly service.
          I'll definitely order again!”
        </p>

        <div class="testimonial-person">
          <div class="testimonial-avatar">A</div>

          <div>
            <h3>Happy Customer</h3>
            <span>Farfad Kitchen Customer</span>
          </div>
        </div>
      </article>

    </div>

  </div>
</section>
      


     <!-- CTA -->
<section class="cta-section">

  <div class="cta-overlay"></div>

  <div class="cta-content">

    <span class="section-label">
      🍽️ READY TO EAT?
    </span>

    <h2>
      Your Next Delicious
      <span>Meal Awaits.</span>
    </h2>

    <p>
      From delicious Nigerian meals to refreshing drinks,
      Farfad Kitchen is ready to serve you something special.
    </p>

    <div class="cta-buttons">

      <a href="#menu" class="cta-primary-btn">
        Explore Our Menu →
      </a>

      <a
        href="https://wa.me/2347012920913"
        target="_blank"
        rel="noopener noreferrer"
        class="cta-secondary-btn"
      >
        💬 Order on WhatsApp
      </a>

    </div>

    <div class="cta-details">

      <span>📍 FHA Lugbe, Abuja</span>

      <span>📞 07012920913</span>

      <span>❤️ Made With Care</span>

    </div>

  </div>

</section>

   <section id="contact" class="contact-section">
  <div class="contact-container">

    <div class="contact-info">

      <p class="section-tag">GET IN TOUCH</p>

      <h2>
        Come Visit
        <span>Farfad Kitchen</span>
      </h2>

      <p class="contact-intro">
        Looking for delicious Nigerian meals in Abuja?
        Come visit us at Farfad Kitchen. We'd love to serve you.
      </p>

      <div class="contact-details">

        <div class="contact-card">
          <div class="contact-icon">📍</div>

          <div>
            <h3>Our Location </h3>
            <p>
              Plot 414, Phase 2, FHA Lugbe,<br>
              Khia Medics Complex,<br>
              by the Police Signboard, Abuja.
            </p>
            <H4>Second Branch</H4>
            <p>
              HOUSE 19, 4th Avenue, PHASE I, FHA, Lugbe, Abuja,
            </p>
          </div>
        </div>

        <div class="contact-card">
          <div class="contact-icon">📞</div>

          <div>
            <h3>Call Us</h3>

            <a href="tel:07012920913">
              07012920913
            </a>

            <a href="tel:09017300030">
              09017300030
            </a>
          </div>
        </div>

        <div class="contact-card">
          <div class="contact-icon">💬</div>

          <div>
            <h3>WhatsApp</h3>

            <a
              href="https://wa.me/2347012920913"
              target="_blank"
              rel="noopener noreferrer"
            >
              Chat with us
            </a>
          </div>
        </div>

      </div>

      <a
        class="direction-btn"
        href="https://www.google.com/maps/search/?api=1&query=Plot+414+Phase+2+FHA+Lugbe+Abuja"
        target="_blank"
        rel="noopener noreferrer"
      >
        📍 Get Directions
      </a>

    </div>

    <div class="contact-visual">

      <img
        src="/images/farfad-building.png"
        alt="Farfad Kitchen"
      >

      <div class="contact-location-card">
        <div class="location-pin">📍</div>

        <div>
          <strong>Farfad Kitchen</strong>
          <span>FHA Lugbe, Abuja</span>
        </div>
      </div>

    </div>

  </div>
</section>

    <div v-if="order.length > 0" class="floating-order">
  <div class="floating-order-info">
    <span class="cart-icon">🛒</span>
    <div>
      <strong>Your Order</strong>
      <small>
        {{ order.reduce((total, item) => total + item.quantity, 0) }} item(s)
      </small>
    </div>
  </div>

  <div class="floating-order-right">
    <strong>₦{{ formatPrice(orderTotal) }}</strong>
    <a href="#menu">View Order</a>
  </div>
</div>


   <footer class="footer">
  <div class="footer-container">

    <!-- BRAND -->
    <div class="footer-brand">
      <img
        src="/images/farfad-logo.png"
        alt="Farfad Kitchen"
      >

      <p>
        Delicious Nigerian meals, refreshing drinks and quality service,
        freshly prepared with care at Farfad Kitchen.
      </p>

      <div class="footer-socials">

        <!-- Instagram -->
        <a
          href="https://www.instagram.com/realfarfad_kitchen?stkn=YmZqeGUxeHJzZ3dx"
          target="_blank"
          rel="noopener noreferrer"
          aria-label="Instagram"
        >
          📷
        </a>

        <!-- TikTok -->
        <a
          href="https://www.tiktok.com/@real_farfad_kitchen?_r=1&_t=ZS-99jmDhLUPMT"
          target="_blank"
          rel="noopener noreferrer"
          aria-label="TikTok"
        >
          🎵
        </a>

        <!-- WhatsApp -->
        <a
          href="https://wa.me/2347012920913"
          target="_blank"
          rel="noopener noreferrer"
          aria-label="WhatsApp"
        >
          💬
        </a>

        <!-- Phone -->
        <a
          href="tel:07012920913"
          aria-label="Call Farfad Kitchen"
        >
          📞
        </a>

      </div>
    </div>


    <!-- QUICK LINKS -->
    <div class="footer-column">
      <h3>Quick Links</h3>

      <a href="#home">Home</a>
      <a href="#menu">Our Menu</a>
      <a href="#about">About Us</a>
      <a href="#gallery">Gallery</a>
      <a href="#contact">Contact</a>
    </div>


    <!-- OUR MENU -->
    <div class="footer-column">
      <h3>Our Menu</h3>

      <a href="#menu">Food</a>
      <a href="#menu">Swallow</a>
      <a href="#menu">Soup</a>
      <a href="#menu">Snacks</a>
      <a href="#menu">Protein</a>
      <a href="#menu">Drinks</a>
      <a href="#menu">Side Food</a>
    </div>


    <!-- CONTACT -->
    <div class="footer-column footer-contact">
      <h3>Visit Us</h3>

      <p>
        📍 Plot 414, Phase 2, FHA Lugbe,
        Khai Medics Complex,
        by the Police Signboard, Abuja.
      </p>

      <a href="tel:07012920913">
        📞 07012920913
      </a>

      <a href="tel:09017300030">
        📞 09017300030
      </a>

      <a
        href="https://wa.me/2347012920913"
        target="_blank"
        rel="noopener noreferrer"
      >
        💬 WhatsApp Us
      </a>

      <a
        href="https://www.instagram.com/realfarfad_kitchen?stkn=YmZqeGUxeHJzZ3dx"
        target="_blank"
        rel="noopener noreferrer"
      >
        📷 Instagram
      </a>

      <a
        href="https://www.tiktok.com/@real_farfad_kitchen?_r=1&_t=ZS-99jmDhLUPMT"
        target="_blank"
        rel="noopener noreferrer"
      >
        🎵 TikTok
      </a>
      <a
      href="https://www.facebook.com/Alamatoreal"
      target="_blank"
      rel="noopener noreferrer"
      >
        <svg viewBox="0 0 48 48" width="20" height="20">
    <rect width="48" height="48" rx="10" fill="#1877F2"/>
    <path d="M31.5 25.5h-5v14h-6v-14h-3.5v-5.2H20.5v-3.4c0-4.1 2-6.6 6.9-6.6h4.4v5.2h-2.8c-1.4 0-1.9.6-1.9 1.9v2.9h4.8l-.4 5.2z" fill="#fff"/>
        </svg>Facebook
        
      </a>
    </div>

  </div>


  <!-- FOOTER BOTTOM -->
  <div class="footer-bottom">

    <div>
      © 2026 <strong>Farfad Kitchen</strong>. All rights reserved.
    </div>

    <div>
      Made with ❤️ for good food.
    </div>

  </div>
</footer>
</template>