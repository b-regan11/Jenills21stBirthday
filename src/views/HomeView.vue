<template>
  <div class="home">
    <h1 class="TopHeader">Jenill's 21st Birthday</h1>
    <p class="TopText">Can You Believe It?</p>
    <p class="MiddleText">Please Join Us For A Birthday Celebration</p>
    <p class="BottomText">If Gifting, Contributions To The College Fund Greatly Appreciated</p>

      <div class="slider">
        <div class="slider-wrapper" :style="{ transform: `translateX(-${currentIndex * 100}%)` }">
          <div v-for="(image, index) in images" :key="index" class="slide">
            <img :src="image" :alt="'Slide ' + index" />
          </div>
        </div>
      </div>
      <div class="eventInfo">
        <p>July 14th | 4:00 pm</p>
        <p>East End Yacht Club</p>
        <p><a href="https://www.google.com/maps/search/?api=1&query=104+Bay+Street,+Bridgeport,+CT" target="_blank">104 Bay Street, Bridgeport, CT</a></p>
        <p>RSVP w/ Will Perez Jr by July 1st</p>
      </div>

  </div>
</template>

<script>
export default {
  data() {
    return {
      currentIndex: 0,
      images: [
        require('@/assets/Jenill1.jpeg'),
        require('@/assets/Jenill2.jpeg'),
        require('@/assets/Jenill3.jpeg'),
        require('@/assets/Jenill4.jpeg'),
        require('@/assets/Jenill5.jpeg'),
      ]
    };
  },
  mounted() {
    this.startSlider();
    this.setRandomStart();
    this.setTitle();
  },
  methods: {
    startSlider() {
      setInterval(() => {
        this.currentIndex = (this.currentIndex + 1) % this.images.length;
      }, 10000); // Change slide every 10 seconds
    },
    setRandomStart() {
      this.currentIndex = Math.floor(Math.random() * this.images.length);
    },
    setTitle() {
      document.title = "Jenill's Birthday";
    }
  }
};
</script>

<style scoped>
.home {
  display: grid;
  background-color: lavenderblush;
  justify-content: center;
  align-items: center;
}

.TopHeader {
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  grid-row: 1;
  font-size: 75px;
  font-family: "Brush Script MT", "Lucida Handwriting", cursive;
  color:palevioletred;
  text-shadow: 
    -1px -1px 0 black,
    1px -1px 0 rgb(141, 132, 84),
    -1px 1px 0 white,
    1px 1px 0 white;
  margin-bottom: 10px;
}

.eventInfo {
  grid-row: 6;
}

.eventInfo p {
    font-family: 'Open Sans', Arial, sans-serif;
    font-size: 18px;
    color: #333;
    margin: 0 0;
    margin-top: 1px;
    justify-content: center;
    align-items: center;
    text-align: center;
    font-size: 24px;
  }

.eventInfo a {
  text-decoration: none;
  color: #333;
  margin: 0 0;
  margin-top: 1px;
  justify-content: center;
  align-items: center;
  text-align: center;
  font-size: 24px;
}

.TopText {
  margin: 0 0;
  justify-content: center;
  align-items: center;
  text-align: center;
  font-size: 22px;
  grid-row: 2;
  font-family: 'Open Sans', Arial, sans-serif;
  color: #333;
}
.MiddleText {
  margin: 0 0;
  justify-content: center;
  align-items: center;
  text-align: center;
  font-size: 20px;
  grid-row: 3;
  font-family: 'Open Sans', Arial, sans-serif;
  color: #333;
}
.BottomText {
  margin: 0 0;
  justify-content: center;
  align-items: center;
  text-align: center;
  grid-row: 4;
  font-size: 20px;
  font-family: 'Open Sans', Arial, sans-serif;
  color: #333;
  margin-bottom: 10px;
}

.slider {
  overflow: hidden;
  width: 415.5px; /* 277px width */
  height: 525px; /* 350px height */
  position: relative;
  
  display: flex; 
  justify-self: center;
  justify-content: center; 
  align-items: center;
  grid-row: 5;
}

.slider-wrapper {
  display: flex;
  transition: transform 0.5s ease;
}

.slide {
  min-width: 100%;
  height: 100%;
}

img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

@media (max-width: 450px) {
  .slider {
    width: 70%;
    max-width: none;
    height: auto;
    margin: 0 auto;
    margin-bottom: 5px;
  }
  .TopHeader {
    margin: 0 0;
    margin-top: 10px;
    font-size: 60px;
  }
  .TopText {
    margin: 0 0;
    justify-content: center;
    align-items: center;
    text-align: center;
    font-size: 20px;
  }
  .MiddleText {
    margin: 0 0;
    justify-content: center;
    align-items: center;
    text-align: center;
    font-size: 16px;
  }
  .BottomText {
    margin: 0 0;
    justify-content: center;
    align-items: center;
    text-align: center;
    font-size: 16px;
    margin-bottom: 5px;
  }
  .eventInfo p {
    margin: 0 0;
    margin-top: 2px;
    justify-content: center;
    align-items: center;
    text-align: center;
    font-size: 20px;
  }
  .eventInfo a {
    margin: 0 0;
    justify-content: center;
    align-items: center;
    text-align: center;
    font-size: 20px;
  }
}

</style>
