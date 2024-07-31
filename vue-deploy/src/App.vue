<template>
  <div class="container">
    <div class="card-container">
      <div class="card" v-for="product in products" :key="product.id">
        <div class="card-header">
          <i
            :class="['fas', 'fa-heart', 'favorite-icon', { active: product.isFavorite }]"
            @click="toggleFavorite(product)"
          ></i>
        </div>
        <img :src="product.image" alt="Product Image" class="card-img-top" />
        <div class="card-body">
          <h3 class="card-title">{{ product.title }}</h3>
          <p class="card-price">{{ product.price }}</p>
          <p class="card-description">{{ product.description }}</p>
          <div class="quantity-controls">
            <button class="quantity-btn" @click="decreaseQuantity(product)">-</button>
            <span class="quantity">{{ product.quantity }}</span>
            <button class="quantity-btn" @click="increaseQuantity(product)">+</button>
          </div>
          <a href="#" class="btn btn-primary"><i class="fas fa-shopping-cart"></i>Add to Cart</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      products: [
        {
          id: 1,
          title: "Product Title 1",
          price: "$99.99",
          description: "Lorem ipsum dolor sit amet consectetur adipisicing elit.",
          image: require('@/assets/images/fried-rice-with-shrimp-prawn-top-white-plate.jpg'),
          quantity: 1,
          isFavorite: false
        },
        {
          id: 2,
          title: "Product Title 2",
          price: "$99.99",
          description: "Lorem ipsum dolor sit amet consectetur adipisicing elit.",
          image: require('@/assets/images/red-spicy-bbq-chicken-cuisine.jpg'),
          quantity: 1,
          isFavorite: false
        },
        {
          id: 3,
          title: "Product Title 3",
          price: "$99.99",
          description: "Lorem ipsum dolor sit amet consectetur adipisicing elit.",
          image: require('@/assets/images/coffee-cup-chocolate-donut-wooden-table.jpg'),
          quantity: 1,
          isFavorite: false
        },
        {
          id: 4,
          title: "Product Title 4",
          price: "$99.99",
          description: "Lorem ipsum dolor sit amet consectetur adipisicing elit.",
          image: require('@/assets/images/green-tea-matcha-latte-white-cup.jpg'),
          quantity: 1,
          isFavorite: false
        },
        {
          id: 5,
          title: "Product Title 5",
          price: "$99.99",
          description: "Lorem ipsum dolor sit amet consectetur adipisicing elit.",
          image: require('@/assets/images/delicious-bread-table.jpg'),
          quantity: 1,
          isFavorite: false
        }
      ]
    };
  },
  methods: {
    toggleFavorite(product) {
      console.log('Toggling favorite for:', product);
      product.isFavorite = !product.isFavorite;
      console.log('New favorite status:', product.isFavorite);
    },
    increaseQuantity(product) {
      product.quantity++;
    },
    decreaseQuantity(product) {
      if (product.quantity > 1) {
        product.quantity--;
      }
    }
  }
};
</script>

<style scoped>
* {
  font-family: 'Helvetica Neue', Arial, sans-serif;
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  background-color: #f4f4f9;
  padding: 2%;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
}

.card-container {
  margin-top: 3%;
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  grid-gap: 20px;
}

.card {
  padding: 20px;
  background: #fff;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  display: flex;
  flex-direction: column;
  transition: transform 0.5s, box-shadow 0.2s;
}

.card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
}

.card-header {
  display: flex;
  justify-content: flex-end;
  align-items: center;
  padding-bottom: 10px;
}

.favorite-icon {
  cursor: pointer;
  color: #ccc;
  transition: color 0.2s;
}

.favorite-icon.active {
  color: #ff6b6b;
}

.card-img-top {
  width: 100%;
  height: 150px;
  object-fit: cover;
  margin-bottom: 10px;
  border-radius: 10px;
}

.card-title {
  color: #333;
  font-size: 20px;
  margin-bottom: 5px;
}

.card-price {
  color: #d11515;
  margin-bottom: 15px;
}

.card-description {
  font-size: 14px;
  color: #777;
  margin-bottom: 15px;
}

.quantity-controls {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 15px;
  font-size: 14px;
}

.quantity-btn {
  color: black;
  border: none;
  cursor: pointer;
  outline: none;
  width: 30px;
  height: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 5px;
  transition: background-color 0.2s;
}

.quantity-btn:hover {
  background-color: #005bb5;
  color: white;
}

.quantity {
  padding: 5px 10px;
  background-color: #eee;
  border-radius: 5px;
  min-width: 40px;
  text-align: center;
}

.btn-primary {
  background-color: #0794fc;
  color: white;
  text-decoration: none;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  transition: background-color 0.2s;
  font-size: 13px;
}

.btn-primary:hover {
  background-color: #005bb5;
}

@media (max-width: 767px) {
  .card-container {
    grid-template-columns: 1fr;
  }

  .card-title,
  .card-price {
    font-size: 16px;
  }
}
</style>
