<template>
  <div class="container">
    <div class="custom-card">
      <div class="img-box">
        <img :src="require(`@/assets/${imageSrc}`)">
      </div>
      <div class="custom-content">
        <h2>{{ title }}</h2>
        <p>{{ description }}</p>
        <a :href="( link )" target="_blank">ver proyecto</a>
      </div>
    </div>
  </div>
</template>

  <script>
  export default {
    props: {
      imageSrc: {
        type: String,
        required: true,
      },
      imageAlt: {
        type: String,
        required: true,
      },
      title: {
        type: String,
        required: true,
      },
      description: {
        type: String,
        required: true,
      },
      link: {
        type: String,
        required: true,
      },
    },
  };
  </script>

  <style scoped>
  .container{
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
    gap: 100px 50px;
    padding: 100px 50px;
  }

  .container .custom-card{
    position: relative;
    display: flex;
    justify-content: center;
    align-items: flex-start;
    width: 350px;
    max-width: 100%;
    height: 300px;
    background: rgba(55, 55, 55, 0.436);
    border-radius: 20px;
    transition: 0.5s;
  }

  .container .custom-card:hover{
    height: 400px;
  }

  .container .custom-card .img-box{
    position: absolute;
    top: 25px;
    width: 300px;
    height: 220px;
    background: #333;
    border-radius: 12px;
    overflow: hidden;
    transition: 0.5s;
  }

  .container .custom-card:hover .img-box{
    top: -100px;
    scale: 0.75;
    box-shadow: 0 15px 45px rgba(0, 183, 255, 0.283);
  }
  .container .custom-card .img-box img{
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  .container .custom-card .custom-content{
    position: absolute;
    top: 235px;
    width: 100%;
    height: 56px;
    padding: 0 30px;
    text-align: center;
    overflow: hidden;
    transition: 0.5s;
  }

  .container .custom-card:hover .custom-content{
    top:80px;
    height: 300px;
  }
  .container .custom-card .custom-content h2{
    font-size: 1.5rem;
    font-weight: 700;
    color: #80DBFF;
  }
  .container .custom-card .custom-content p{
    color: #ebebeb;
  }
  .container .custom-card .custom-content a{
    position: relative;
    top: 15px;
    display: inline-block;
    padding: 12px 25px;
    text-decoration: none;
    background: #F1916D;
    color: #ebebeb;
    font-weight: 500;
  }

  .container .custom-card .custom-content a:hover{
    opacity: 0.8;
  }

  </style>
