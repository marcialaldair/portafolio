<template>
  <div id="app">
    <nav class="navbar">
    <div class="container">
      <div class="nav-links">
          <router-link @click="scrollToSection('inicio')" class="nav-link" :class="{ 'active-link': currentSection === 'inicio' }">Inicio</router-link>
          <router-link @click="scrollToSection('about')" class="nav-link" :class="{ 'active-link': currentSection === 'about' }">Acerca de mí</router-link>
          <router-link @click="scrollToSection('experience')" class="nav-link" :class="{ 'active-link': currentSection === 'experience' }">Experiencia</router-link>
          <!-- <router-link @click="scrollToSection('contact')" class="nav-link" :class="{ 'active-link': currentSection === 'contact' }">Contacto</router-link> -->
        </div>
    </div>
    <button class="download-cv right-aligned" @click="descargarCV">Descargar CV</button>
  </nav>
        <div class="banner" id="inicio">
        <div class="banner-text">
          <div class="banner-gradient"></div>
          <h1>Aldair<br>Marcial</h1>
          <p>Un <span class="colored-text">desarrollador web frontend</span> de Veracruz,Mex</p>
        </div>
      </div>
      <div id="about">
        <div class="sections">
          <p>Acerca de mi</p>
        </div>
        <div class="acercademi">
          <img src="../src/assets/foto_perfil.jpg" alt="">
          <p>
            ¡Hola y bienvenid@! Permíteme presentarme, soy Aldair Marcial Reyes, egresado del Instituto Tecnológico de Veracruz, donde cursé la carrera de
            <b>Ingeniería en Sistemas Computacionales</b>. Me apasiona el desarrollo web, especialmente la especialización en frontend y el área de UX/UI.
            Disfruto colaborar con personas de diferentes partes del mundo, lo cual ha sido posible gracias a mi trabajo tanto a nivel nacional como internacional.<br><br>
            Además, quiero destacar que soy una persona responsable, capaz de asumir liderazgo si es necesario.
            Estoy completamente dispuesto a seguir órdenes y aportar en equipo para alcanzar nuestros objetivos.
            Tengo una sed constante de aprendizaje y estoy abierto a nuevas herramientas y tecnologías.
            Mi capacidad de aprender de forma rápida y autodidacta me ha permitido adaptarme ágilmente a los desafíos que se presentan en el desarrollo tecnológico.<br><br>
            Si hay algo más en lo que pueda ayudarte o si deseas saber más sobre mi experiencia y habilidades, ¡no dudes en preguntar! <br>
            <br> <b>Nombre:</b> Aldair Marcial Reyes
            <br> <b>Telefono: </b>2291404150
            <br> <b>Email: </b> marcialaldair@gmail.com
            <br> <b>Ubicación: </b>Boca del Río, Veracruz. México
          </p>
        </div>
      </div>
      <div id="experience">
        <div class="sections">
          <p>Experiencia</p>
        </div>
      <div class="experiencia">
        <ExperienceCard
          v-for="(experience, index) in experiences"
          :key="index"
          :experience="experience"
          :borderColor="borderColor[index]"
          :backgroundColor="backgroundColor[index]"
          :alternativeTextColor="alternativeColor[index].text"
          :alternativeColor="alternativeColor[index].background"
          :titleCard="experience.titleCard"
          :alternativeText="experience.alternativeText"
        ></ExperienceCard>
      </div>
    </div>
      <div class="sections">
        <p>Lenguajes,herramientas y frameworks</p>
      </div>
      <div class="misc">
        <img src=".\assets\html-5.png" title="HTML">
        <img src=".\assets\css-3.png" title="CSS">
        <img src=".\assets\js.png" title="Javascript">
        <img src="./assets/img_bootstrap.png" title="Bootstrap">
        <img src="./assets/vue.png" title="Vue">
        <img src="./assets/figma.png" title="Figma">
      </div>
      <div class="misc">
        <img src="./assets/github.png" title="Github">
        <img src="./assets/gitlab.png" title="Gitlab">
        <img src="./assets/DBeaver.svg" title="DBeaver">
        <img src="./assets/icons8-potencia-shell-48 1.png" title="Powershell">
        <img src="./assets/php.png" title="PHP">
        <img src="./assets/svn.svg" title="SVN">
      </div>
      <div class="misc">
        <img src="./assets/mysql.png" title="MySQL">
        <img src="./assets/icons8-python-48 1.png" title="Python">
        <img src="./assets/icons8-power-bi-48 1.png" title="PowerBI">
        <img src="./assets/Purview.svg" title="Puview">
        <img src="./assets/ubuntu.png" title="Ubuntu">
        <img src="./assets/photoshop.png" title="Photoshop">
      </div>
      <div class="misc">
        <img src="./assets/pandas_white.svg" title="pandas">
        <img src="./assets/NumPy.svg" title="NumPy">
        <img src="./assets/postman.png" title="Postman">
        <img src="./assets/wordpress.png" title="Wordpress">
      </div>
      <div class="sections">
        <p>Proyectos</p>
      </div>
        <div class="cardProjects">
          <CardProject
            v-for="(project, index) in projects"
            :key="index"
            :imageSrc="project.imageSrc"
            :imageAlt="project.imageAlt"
            :title="project.title"
            :description="project.description"
            :link="project.link"
          ></CardProject>
        </div>
      <div class="sections">
        <p>Certificados</p>
      </div>
      <div class="certificates">
        <img src="./assets/ilustracion_pd.png">
        <img src="./assets/diseño_IU.png">
        <img src="./assets/diploma_wordpress.png">
      </div>
      <!-- <div class="sections" id="contact">
        <p>Contacto</p>
      </div> -->
      <footer>
    <div class="footer-left">
        Diseñado por <b>Aldair Marcial</b> | Hosteado en <b>Netlify</b>
    </div>
    <div class="footer-right">
        <span>&#9888;</span> La página sigue en desarrollo y mejora constante <span>&#9888;</span>
    </div>
</footer>
  </div>
</template>

<script>
import ExperienceCard from '@/components/ExperienceCard.vue';
import CardProject from '@/components/CardProject.vue';
import FileSaver from 'file-saver';

export default {
  components: {
    ExperienceCard,
    CardProject
  },
  watch: {
    $route(to) {
      this.currentRoute = to.path;
    },
  },
  methods: {
    descargarCV() {
      fetch('public/CV_Aldair_Marcial_Reyes.pdf', {
        responseType: 'arraybuffer'
      })
      .then((response) => {
        console.log(response);
        const blob = new Blob([response.data], { type: 'application/pdf' });
        FileSaver.saveAs(blob, 'CV_Aldair_Marcial_Reyes.pdf');
      });
    },
    scrollToSection(sectionId) {
      const element = document.getElementById(sectionId);
      if (element) {
        element.scrollIntoView({ behavior: "smooth" });
      }
    },
    handleScroll() {
      const scrollPosition = window.scrollY;
      const aboutPosition = document.getElementById('about').offsetTop - 3;
      const experiencePosition = document.getElementById('experience').offsetTop - 3;
      // const contactPosition = document.getElementById('contact').offsetTop - 3 ;

      if (scrollPosition < aboutPosition) {
        this.currentSection = 'inicio';
      } else if (scrollPosition < experiencePosition) {
        this.currentSection = 'about';
      } else if (scrollPosition /*< contactPosition*/) {
        this.currentSection = 'experience';
      } //else {
      //   this.currentSection = 'contact';
      // }
    },
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll);
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.handleScroll);
  },
  data() {
    return {
      currentSection: 'inicio',
      experiences: [
        {
          imageSrc: 'tantan.png',
          imageAlt: 'Descripción 1',
          date: 'Enero - Junio 2022 ',
          alternativeText:'Esta empresa se especializa en el desarrollo de credenciales digitales para diversas instituciones mediante la tecnología blockchain. Mi responsabilidad principal consistía en gestionar incidentes reportados por los clientes, lo que implicaba acceder regularmente a la base de datos utilizando DBeaver. Además, participaba activamente en el diseño y mejora de las credenciales, lo que incluía realizar modificaciones en HTML y CSS para optimizar su apariencia y funcionalidad.',
          titleCard:'Tan Tan',
          tools:['html-5.png','css-3.png','gitlab.png','DBeaver.svg']
        },
        {
          imageSrc: 'ebcomm.png',
          imageAlt: 'Descripción 1',
          date: 'Junio - Diciembre 2022',
          alternativeText:'La empresa se enfoca en el desarrollo de soluciones de e-commerce. Durante mi tiempo allí, lideré un proyecto de una tienda en línea. Esta experiencia me brindó una sólida exposición al desarrollo web, donde implementé el modelo MVC. Para el diseño, empleaba Figma para crear propuestas visuales, las cuales luego transformaba en código utilizando HTML, CSS y JS con el apoyo del framework Bootstrap. Este proceso se integraba con PHP para interactuar con una base de datos mediante consultas SQL. Finalmente, para gestionar versiones y subir cambios, utilizaba SVN.',
          titleCard:'EBCOMM',
          tools:['html-5.png','css-3.png','js.png','img_bootstrap.png','figma.png','svn.svg','mysql.png','php.png']
        },
        {
          imageSrc: 'tenaris.png',
          imageAlt: 'Descripción 1',
          date: 'Febrero 2023 - Enero 2024',
          alternativeText:"La empresa se centra en la fabricación de tubos sin costura. Mi rol se encontraba en el área de BI & Analytics tools, donde llevé a cabo una variedad de tareas que me permitieron desarrollar nuevas habilidades. Entre estas tareas, se incluyó el consumo de API's de Purview para realizar modificaciones en Databricks y datalakes, utilizando Python para el manejo de archivos JSON. Además, realizaba la manipulación de datos utilizando las bibliotecas Pandas y NumPy. Finalmente, desarrollé varios scripts en PowerShell para automatizar diversas tareas dentro del proceso.",
          titleCard:'Tenaris Tamsa',
          tools:['icons8-python-48 1.png','icons8-power-bi-48 1.png','icons8-microsoft-excel-2019-48 1.png','icons8-potencia-shell-48 1.png','Purview.svg','pandas_white.svg','NumPy.svg']
        },
      ],
      backgroundColor: ['#30323C','#313038','#28244D'],
      borderColor:['#F07F38','#F37321','#CA358B'],
      alternativeColor: [
        { text: '#FFF', background: '#040400' },
        { text: '#FFF', background: '#373737' },
        { text: '#FFF', background: '#373737' },
      ],
      projects:[
        {
          imageSrc:'ilumcam.png',
          imageAlt:'nada',
          title:'Iluminando caminos',
          description:'Pagina tipo blog realizada para la psicologa Rosa Laura Torres Díaz el cual contiene una pagina principal con información basica acerca de ella y sus consultas. Una sección de blog en la cual se pueden leer publicaciones y una parte de administración para programar las publicaciones,editarlas o borrarlas',
          link:'https://iluminandocaminos.blog/'
        },
        {
          imageSrc:'API_Rick&Morty.png',
          imageAlt:'nada',
          title:'Consumo de API con Vue',
          description:'Este fue un proyecto que hice para aprender el cosumo de APIs y VUE esta desplegado en netlify',
          link:'https://rick-and-morty-aldair.netlify.app/'
        }
      ]
    };
  },
};
</script>

<style>
  body {
    background-color: #06142E;
    margin: 0;
    font-family: 'Nunito', sans-serif;
  }

  /* Estilos para la barra de navegación */
  .navbar {
    padding: 23px 0;
    position: sticky;
    top: 0;
    z-index: 100;
    display: flex;
    justify-content: center; /* Alinea los elementos hacia los extremos */
    align-items: center; /* Alinea verticalmente al centro */
    background: #06142E;
  }

  .container{
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .nav-links {
  font-size: 19px;
  display: flex;
  gap: 30px;
  cursor: pointer;
  color: var(--science-ble, #80DBFF);
  font-style: normal;
  font-weight: 700;
  line-height: 84.9%;
  letter-spacing: 2.275px;
  text-decoration: none; /* Para quitar el subrayado predeterminado de los enlaces */
  transition: border-bottom 0.3s ease; /* Transición suave para el subrayado */
  position: relative;
}

.nav-link {
  position: relative;
}

.nav-link::after {
  content: "";
  position: absolute;
  width: 0;
  height: 3px; /* Grosor del subrayado */
  background-color: #80DBFF; /* Color del subrayado */
  left: 50%;
  bottom: -5px;
  transition: all 0.3s ease-in-out;
  border-radius: 10px;
}

.nav-link:hover {
  text-shadow: 0px 3px 15px #0075DB, 0px 3px 15px #0075DB;
  cursor: pointer;
}

.nav-link:hover::after {
  width: 100%;
  left: 0;
}

.active-link {
  text-shadow: 0px 3px 15px #0075DB, 0px 3px 15px #0075DB;
  cursor: pointer;
}

  .download-cv {
    font-family: 'Nunito', sans-serif;
    font-size: 20px;
    border-radius: 10px;
    background: rgba(217, 217, 217, 0.20);
    color: #F2F2F2;
    padding: 5px 20px;
    border: none;
    cursor: pointer;
    margin-left: auto; /* Empujar el botón hacia la derecha */
  }

  .right-aligned {
    position: absolute;
    right: 27px;
  }

  /* Estilos para el banner */
  .banner {
  background:
  linear-gradient(
    to right,
    rgba(0, 0, 0, 0.5),
    rgba(0, 0, 0, 0)
  ),
  url('/src/assets/banner_3.jpeg');
  background-size: cover;
  background-position: center;
  height: 95vh; /* Se ajusta a la altura de la ventana */
  display: flex;
  align-items: center;
  justify-content: center;
  color: #F2F2F2;
  text-align: center;
  position: relative;
}

.banner-text {
  max-width: 90%;
  padding: 0 20px; /* Añadido relleno para adaptarse a diferentes tamaños de pantalla */
  position: absolute; /* Añadido */
  bottom: 20px; /* Añadido */
  left: 28%; /* Añadido */
  transform: translateX(-50%); /* Añadido */
}

.banner-text h1 {
  font-size: 7vw; /* Cambiado a vw para que sea responsive */
  letter-spacing: 0.8vw; /* Cambiado a vw para que sea responsive */
  margin-bottom: 1vw; /* Cambiado a vw para que sea responsive */
  text-align: left;
}

.banner-text p {
  font-size: 1.8vw; /* Cambiado a vw para que sea responsive */
  margin-bottom: 3vw; /* Cambiado a vw para que sea responsive */
  letter-spacing: 0.2vw; /* Cambiado a vw para que sea responsive */
  text-align: left;
}

.colored-text {
  color: #80dbff;
}

@media screen and (max-width: 768px) {
  .banner-text h1 {
    font-size: 6vw;
    letter-spacing: 0.6vw;
    margin-bottom: 4vw;
  }

  .banner-text p {
    font-size: 1.5vw;
    margin-bottom: 2vw;
    letter-spacing: 0.15vw;
  }
}

@media screen and (max-width: 480px) {
  .banner-text h1 {
    font-size: 10vw;
    letter-spacing: 1vw;
    margin-bottom: 6vw;
  }

  .banner-text p {
    font-size: 3vw;
    margin-bottom: 4vw;
    letter-spacing: 0.3vw;
  }
}


/* Estilos de las secciones del portfolio */
  .sections{
    display: flex;
    text-align: center;
    justify-content: center;
    color: #80dbff;
    font-size: 25px;
    font-style: normal;
    font-weight: 700;
    line-height: 84.9%; /* 27.168px */
    letter-spacing: 2.08px;
    padding-top: 100px;

  }

    .sections p {
    position: relative;
  }

  .sections p::after {
    content: '';
    display: block;
    width: 100%;
    height: 3px;
    background-color: #80dbff;
    position: absolute;
    bottom: -6px;
    left: 0;
    border-radius: 5px;
  }

  /* Estilos de seccion acerca de mi */

    .acercademi{
      display: flex;
      align-content: center;
      align-items: center;
      padding: 60px;
    }
    .acercademi p{
      color: #F2F2F2;
      padding-left:40px ;
    }

    .acercademi img{
      width: 480px;
      height: 480px;
      border-bottom: 15px solid #80dbff;
      border-right: 15px solid #80dbff;
      border-radius: 18px;
    }

    /* Card de las empresas */

    .experiencia{
      padding-left: 30px;
      padding-right: 30px;
      display: flex;
      flex-direction: row;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
    }

    /* simbolos de herramientas */
    .misc{
      padding-top: 40px;
      padding-left: 100px;
      padding-right: 100px;
      display: flex;
      flex-direction: row;
      align-items: center;
      justify-content: space-around;
    }

    .misc img{
      width: 64px;
      height: 64px;
    }

    /* Card de proyectos */
    .cardProjects{
      padding-left: 30px;
      padding-right: 30px;
      display: flex;
      flex-direction: row;
      align-items: center;
      flex-wrap: wrap;
      justify-content: center;
    }

    .certificates{
      padding-left: 30px;
      padding-right: 30px;
      display: flex;
      flex-direction: row;
      align-items: center;
      justify-content: center;
      flex-wrap: wrap;
    }

    .certificates img{
      height: 350px;
      padding: 40px;
    }

    footer {
    background-color: #001F3D;
    padding: 45px 0;
    text-align: center;
    justify-content: center;
    box-shadow: 0 15px 45px rgba(0, 183, 255, 0.528);
}

.footer-left {
    float: left;
    color: #F2F2F2;
}

.footer-right {
    float: right;
    color: #F2F2F2;
}

/* Estilos opcionales para mejorar la apariencia */
.footer-left,
.footer-right {
    width: 50%;
}

/* Estilos para hacer el footer responsivo en dispositivos móviles */
@media screen and (max-width: 768px) {
    .footer-left,
    .footer-right {
        width: 100%;
        float: none;
    }
}

@media screen and (max-width:880px){
  .experiencia{
    justify-content: center;
    align-items: center;
  }
}

@media screen and (max-width:880px){
  .acercademi{
    flex-direction: column;
  }
  .acercademi img{
    width: 400px;
  }
}

@media screen and (max-width:880px){
  ExperienceCard{
    padding-bottom: 100px;
  }
}


</style>
