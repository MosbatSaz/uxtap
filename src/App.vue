<template>
  <v-app class="d-flex justify-center grey darken-4">

  <!-- Dev Mode Viewport Recognition -->
     <v-tooltip color="deep-purple mon darken-4 mon" left>
      <template  v-slot:activator="{ on }">
          <v-btn

          class="deep-purple mon darken-4 white--text"
          v-on="on"
          fab
          bottom
          right
          fixed
          v-resize="onResize">
            {{viewport}}
          </v-btn>
      </template>
      <span class="font-weight-bold orange--text">Dev Mode </span>
      <span> Viewport Recognition</span>
    </v-tooltip>

<!-- scroll up -->
          <!-- <v-fab-transition>
          <v-btn
          v-scroll-to="{
                          el: '#toolBar',
                          duration: 1000,
                          easing: 'ease-in-out',
                          offset: 0,
                          force: true,
                          cancelable: true,
                          onStart: onStart,
                          onDone: onDone,
                          onCancel: onCancel,
                          x: false,
                          y: true

                      }"   
          v-scroll="onScroll"     
          transition="fab-transition"      
          class="deep-purple mon darken-4 white--text"
          v-show="showBtn"
          v-on="on"
          fab
          bottom
          right
          fixed
          >
            
            <v-icon>mdi-chevron-up</v-icon>
          </v-btn>
          
          </v-fab-transition> -->
     


  <!-- Toolbar -->
  
    
  
     <v-app-bar   elevate-on-scroll fixed id="toolBar"   :height="(viewport == 'xs')?80:120" class="toolb ma-0 pa-0 white pb-10">

      <img  :class="`${(viewport == 'xs') ? 'ml-3':'ml-12'} `" :height="(viewport == 'xs') ? 50:70"  src="./assets/ux tap logo.png" />

      <v-spacer></v-spacer>

      <a :href="worksUrl">
      <v-btn 
      
      height="80"
      :ripple="true"  
      class=" 'mx-3' deep-purple--text text--darken-3  transparent text-capitalize   hidden-sm-and-down" 
      text>

      <v-row class="pa-0" justify="center" align="center">
       
       <v-col class="ma-0 pa-0 mb-2"  cols="12"><v-icon color="deep-purple darken-3">mdi-collage</v-icon></v-col>
       <v-col class=" ma-0 pa-0 grey--text text--darken-3" cols="12"><span>My Works</span></v-col>

      </v-row>
   
      </v-btn>
      </a>
  
      <v-btn 
      v-scroll-to="{
                el: item.target,
                duration: 1000,
                easing: 'ease-in-out',
                offset: -200,
                force: true,
                cancelable: true,
                onStart: onStart,
                onDone: onDone,
                onCancel: onCancel,
                x: false,
                y: true

            }"
      height="80"
      :ripple="true"  
      v-for="(item,i) in items" :key="i" 
      :href="(i==0)?'':''"
      :class="`${(i == 4)?'mr-12 ml-12' : 'mx-3'} deep-purple--text text--darken-3  transparent text-capitalize   hidden-sm-and-down`" 
      text>

      <v-row class="pa-0" justify="center" align="center">
       
       <v-col class="ma-0 pa-0 mb-2"  cols="12"><v-icon color="deep-purple darken-3">{{item.icon}}</v-icon></v-col>
       <v-col class=" ma-0 pa-0 grey--text text--darken-3" cols="12"><span>{{item.title}}</span></v-col>

      </v-row>
   
      </v-btn>
      

      <v-app-bar-nav-icon 
      x-large
      @click="drawer = !drawer"
      class="transparent grey--text text--darken-3 mr-1  hidden-md-and-up" >
      </v-app-bar-nav-icon>
      
     </v-app-bar>


  <!-- Navigation Drawr -->
  <v-navigation-drawer 
  floating
  right 
  app 
  class="hidden-md-and-up"
  width="200"
  v-model="drawer">
  <v-row class="pa-0 " justify="center" align="start" no-gutters>
  <v-img class="h100v d-flex justify-center" src="./assets/Beautiful.png">



  <v-col
  cols="12"
  class="ma-0 pa-0">
  <a :href="worksUrl">
   <v-btn 
      @click="drawer = !drawer"
      tile
      height="80"
      width="200"
      :ripple="true"  
      class="d-inline-block white--text ma-0 pa-0   transparent text-capitalize" 
      text>
      

        <v-icon color="white darken-3 ">mdi-collage</v-icon>
        <span class="grey--text text--lighten-2 ml-2">My Works</span>
        
      
      </v-btn>
  </a>
  </v-col>

  <v-col cols="12"
  class="ma-0 pa-0"
  v-for="(item,i) in items" :key="i" 

  >


 
    <v-btn 
          v-scroll-to="{
                el: item.target,
                duration: 1000,
                easing: 'ease-in-out',
                offset: -100,
                force: true,
                cancelable: true,
                onStart: onStart,
                onDone: onDone,
                onCancel: onCancel,
                x: false,
                y: true

            }"
      @click="drawer = !drawer"
      tile
      :absolute="(i == 3) ? true : false"
      bottom
      height="80"
      width="200"
      :ripple="true"  
      class="d-inline-block white--text ma-0 pa-0   transparent text-capitalize" 
      text>
      

        <v-icon color="white darken-3 ">{{item.icon}}</v-icon>
        <span class="grey--text text--lighten-2 ml-2">{{item.title}}</span>
        
      
      </v-btn>
      
    </v-col>
    </v-img>
  </v-row>
  </v-navigation-drawer>

  <v-card flat :height="(viewport == 'xs')? 50 : 100"> 

  </v-card>

  <!-- Introduce Me -->
  <v-card flat class=" my-12">
    <v-row class="ma-0 pa-0  mx-12 " justify="center" align="top">
      <v-col
      class="mon ma-0 pa-0"
      cols="12"
      sm="6"
      md="4"
      lg="3">

        <v-card flat :class="`${(viewport == 'sm') ? 'display-1':'display-2'}`">Hi I'm Amir</v-card >
        <v-card flat  :class="`${(viewport == 'sm') ? 'headline':'display-1'} mb-2`">Im a UX Designer</v-card >
        <v-card flat max-width="300" :class="`${(viewport == 'sm') ? 'body-1':''}`">Lorem ipsum dolor sit amet consectetur 
          adipisicing elit. Aperiam consequuntur possimus 
          incidunt dignissimos ipsum eos commodi aliquam maxime 
          qui error deserunt quo ipsa architecto nulla,
           molestias enim  saepe. Quo!</v-card >
        <v-card flat max-width="300" :class="`${(viewport == 'sm') ? 'body-1':''} mt-1 `">
         <v-btn           v-scroll-to="{
                          el: '#work',
                          duration: 1000,
                          easing: 'ease-in-out',
                          offset: -100,
                          force: true,
                          cancelable: true,
                          onStart: onStart,
                          onDone: onDone,
                          onCancel: onCancel,
                          x: false,
                          y: true
                      }" 
         class=" text-capitalize hidden-sm-and-up  px-1 deep-purple lighten-4 deep-purple--text elevation-1">
          Know Me Better</v-btn></v-card >

      </v-col
      >
      <v-col
      class="hidden-xs-only ma-0 pa-0"
      cols="8"
      sm="6"
      md="4"
      lg="3">
      <img :class="`${(viewport == 'xs') ? 'w100':''}`" 
      :width="mew" 
      src="./assets/Me Picture.png"
      />
      </v-col>
    </v-row>
  </v-card>  

  <!-- See My Works -->
    <v-card class="ma-0 pa-0" :height="bannerH"
    flat
    tile>
      <!-- <v-img  :height="bannerH"
      src="./assets/Banner@2x.png">

      </v-img> -->

        <v-parallax class="relative" :height="bannerH" src="./assets/banner.png">
          <v-card flat
          class="transparent">
          
            <v-hover
            v-slot:default="{ hover }"
            >
              <v-btn :href="worksUrl" :elevation="(hover == true) ? 24:8" :width="(viewport == 'xs') ? 237:380" :height="(viewport == 'xs') ? 75:120" class="smw">
                <img :height="(viewport == 'xs') ? 30:50" class="mr-1" src="./assets/my works icon.png" />
                <span :class="`${(viewport == 'xs') ? 'title':'display-1' } ml-3 text-capitalize  font-weight-black`">See My Works</span>
              </v-btn>
            </v-hover>
          
          </v-card>
        </v-parallax>
        
    </v-card>
  

  <!-- Know Me Better -->

    <v-card             flat class="text-center mon mt-8 hidden-xs-only">
      <v-btn 
      v-scroll-to="{
                          el: '#work',
                          duration: 1000,
                          easing: 'ease-in-out',
                          offset: -200,
                          force: true,
                          cancelable: true,
                          onStart: onStart,
                          onDone: onDone,
                          onCancel: onCancel,
                          x: false,
                          y: true

                      }"  text rounded height="60" class=" deep-purple--text">
        <v-row class="pa-0 ma-0 py-3" justify="center" align="center">
          <v-col class=" ma-0 pa-0 mb-n1  deep-purple--text text--darken-3" cols="12"><span>Know Me Better</span></v-col>
          <v-col class="ma-0 pa-0" cols="12"><v-icon color="deep-purple darken-3" large>mdi-chevron-down</v-icon></v-col>
        </v-row>
      </v-btn>
    </v-card>





  <!-- My Works -->
  <v-card flat class="ma-0 pa-0  mt-12" height="">

    <!-- <v-img  src="./assets/Back Dot.png"> -->
    
    <div id="work" class="text-center my-12 display-2 font-weight-bold">
    How I Work
    </div>








            <!-- Works -->
              <div v-for="(how,i) in hows" :key="i" class="d-flex justify-center ma-12">
              <v-card 
              :width="(viewport == 'xs') ? '' : 965 " 
              :height="(viewport == 'xs') ? '' : '' "
              min-height="376"
              class="transparent elevation-0">
              <div class="wcard">
                <img 
                :src="how.dot"
                class="cdot"/>

                <span class="display-2 cardNum pt-6 pl-6 font-weight-bold">{{i+1}}</span>

                <v-row justify="center" class="ma-0 pa-6 pl-12">

                  <v-col :cols="12" class="hidden-sm-and-up">
                        <span class=" headline font-weight-bold ">{{how.title}}</span>
                  </v-col>
                  
                  <v-col :cols="(viewport == 'xs')?12:6" 
                  class="hidden-xs-only">

                    <span 
                    class=" display-1 font-weight-bold">
                    {{how.title}}</span>
                    <span class="d-inline-block title font-weight-light">
                      {{how.description}}
                    </span>
                  </v-col>

                  <v-col :cols="(viewport == 'xs')?12:6"
                  class="d-flex justify-center ">
                    <v-img 
                    contain
                    max-height="300"
                    :src="how.img"
                    class="m-12"></v-img>
                  </v-col>

                  <v-col :cols="(viewport == 'xs')?12:6"
                  class="hidden-sm-and-up">

                    <span 
                    class="hidden-xs-only display-1 font-weight-bold">
                    {{how.title}}</span>
                    <span class="d-inline-block title font-weight-light">
                      {{how.description}}
                    </span>
                  </v-col>

                </v-row>

              </div>  
              </v-card>
              </div>

    <!-- </v-img> -->
  </v-card>





  <!-- My Skills -->
    <div id="skill" class="text-center my-12 display-2 font-weight-bold">
    My Skills
    </div>

    <v-card flat class="d-flex justify-center mb-12 transparent">
    <v-card 
    flat
    class="transparent"
    :max-width="skillW">
    <v-row  class="mx-3"  justify="center" align="center">
      <v-col 
      v-for="(skill,i) in skills" :key="i" 
      cols="12" 
      sm="12" 
      md="6" 
      lg="4"
      class="d-flex justify-center">
        <v-card 
        flat
        class="transparent"
        :height="(viewport == 'md') ? 193 : 'auto'"
        width="421">
          <div class="wcard">
            <v-row class="pa-3 px-5">
              <v-col cols="7">
                  <span class="d-inline-block font-weight-black title">{{skill.title}}</span>
                  <span class="d-inline-block">{{skill.description}}</span>
              </v-col>
              <v-col cols="5">
                <v-img
                contain
                :max-height="140"
                :src="skill.img"></v-img>
              </v-col>
            </v-row>
          </div>
        </v-card>
      </v-col>
    </v-row>
  </v-card>
  </v-card>


  <!-- Tools I Use -->
   <div id="tool" class="text-center my-12 display-2 font-weight-bold">
    My Tools
    </div>

    <v-card flat class="d-flex justify-center mb-12 transparent">
    <v-card 
    flat
    class="transparent mb-12"
    :max-width="toolW">
    <v-row  class="mx-3"  justify="center" align="center">
      <v-col 
      v-for="(tool,i) in tools" :key="i" 
      cols="6" 
      sm="6" 
      md="4" 
      lg="3"
      class="d-flex justify-center">
        <v-card 
        flat
        class="transparent"
        :height="200"
        width="200">
          <div class="wcard">
            <v-row class="pa-3 px-5">
                <v-col cols="12">
                <v-img
                contain
                :max-height="80"
                :src="tool.img"></v-img>
              </v-col>

              <v-col cols="12" class="text-center">
                  <span :class="` ${(i >= 1 && i <= 3) ? 'body-1':''} d-inline-block font-weight-black title`">{{tool.title}}</span>
              </v-col>

            </v-row>
          </div>
        </v-card>
      </v-col>
    </v-row>
  </v-card>
  </v-card>
  
  <!-- Footer -->
  <v-card id="footer" class="footer d-flex justify-center">
    <v-img max-height="500" src="./assets/Beautiful.png"
    class="d-flex justify-center ma-0 pa-0">
    <v-card
    flat
    class="transparent my-12 d-flex"
    :max-width="(viewport == 'xs') ? 400 : 996">

      <v-card :max-width="footerW" class="transparent d-flex justify-center mx-12" flat>
      <v-row justify="start" class="ma-0 pa-0" no-gutters>

        <v-col cols="12" class="mb-6"><span :class="` ${(viewport == ('xs'))?'display-2':'display-3'}  font-weight-black white--text`">Contact Me</span></v-col>
        <v-col cols="12" class="mb-1"><span :class="` ${(viewport == ('xs'))?'headline':'display-1'}  font-weight-light white--text`">Amir.ivno@Gmail.com</span></v-col>
        <v-col cols="12" class="mb-8"><span :class="` ${(viewport == ('xs'))?'headline':'display-1'}  font-weight-light white--text`">+98 916 994 8770</span></v-col>
        <v-col cols="12" class="mb-2"><span class=" mb-5 headline white--text">Find Me On</span></v-col>
        <v-col cols="12"><div>

        
           
        <v-btn 
        v-for="(account,i) in accounts"  :key="i"
        :href="account.url"
        icon
        :ripple="false"
        class="mr-8"
        large>
          <v-avatar size="50" tile>
            <v-img :src="account.img"></v-img>
          </v-avatar>
        </v-btn>

        </div></v-col>

      </v-row>
      </v-card>


    </v-card>
    </v-img>
  </v-card>


  </v-app>
</template>



<script>

  
 
  export default {

    data: () => ({
      viewport: '',
      showBtn:false,
      drawer:false,
      items:[
        {title:'How I Work',icon:'mdi-cellphone-link',target:'#work'},
        {title:'My Skills',icon:'mdi-cards',target:'#skill'},
        {title:'Tools I Use',icon:'mdi-tools',target:'#tool'},
        {title:'contact me',icon:'mdi-auto-fix',target:'#footer'}
      ],
      mew:0,
      bannerH:0,
      worksUrl:'https://www.google.com',
      hows:[
        {title:'Start from the End',description:'what I doing is really im doing is really important thing to do',img:require('./assets/work1.png'),dot:require('./assets/dot1.svg')},
        {title:'Define the Problems & Ideation',description:'what I doing is really im doing is really important thing to do',img:require('./assets/work2.png'),dot:require('./assets/dot2.svg')},
        {title:'Wireframing & Prototyping',description:'what I doing is really im doing is really important thing to do',img:require('./assets/work3.png'),dot:require('./assets/dot3.svg')},
        {title:'testing',description:'what I doing is really im doing is really important thing to do',img:require('./assets/work4.png'),dot:require('./assets/dot4.svg')},
        {title:'Shape the final Product',description:'what I doing is really im doing is really important thing to do',img:require('./assets/work5.png'),dot:require('./assets/dot5.svg')},
        {title:'Ready for Development',description:'what I doing is really im doing is really important thing to do',img:require('./assets/work6.png'),dot:require('./assets/dot6.svg')},
      ],
      skills:[
        {title:'Critical Thinking & Problem Solving',description:'what I doing is really im doing is really important thing to do',img:require('./assets/skill1.png')},
        {title:'UX Research',description:'what I doing is really im doing is really important thing to do',img:require('./assets/skill2.png')},
        {title:'User Empathy',description:'what I doing is really im doing is really important thing to do',img:require('./assets/skill3.png')},
        {title:'Collaboration',description:'what I doing is really im doing is really important thing to do',img:require('./assets/skill4.png')},
        {title:'Story Telling',description:'what I doing is really im doing is really important thing to do',img:require('./assets/skill5.png')},
        {title:'Wireframing & UI Prototyping',description:'what I doing is really im doing is really important thing to do',img:require('./assets/skill6.png')},
        {title:'Analytics',description:'what I doing is really im doing is really important thing to do',img:require('./assets/skill7.png')},
        {title:'Web Core Skills',description:'what I doing is really im doing is really important thing to do',img:require('./assets/skill8.png')},
        {title:'Front End Frameworks',description:'what I doing is really im doing is really important thing to do',img:require('./assets/skill9.png')}
      ],
      skillW:'',
      tools:[
        {title:'Adobe XD',img:require('./assets/adobe xd.png')},
        {title:'Adobe Photoshop',img:require('./assets/adobe photoshop.png')},
        {title:'Adobe After Effects',img:require('./assets/adobe after effects.png')},
        {title:'Adobe Illustrator',img:require('./assets/adobe illustrator.png')},
        {title:'Canva',img:require('./assets/canva.png')},
        {title:'VS Code',img:require('./assets/vs code.png')},
        {title:'GitHub',img:require('./assets/github.png')},
        {title:'Postman',img:require('./assets/postman.png')},
      ],
      toolW:'',
      accounts:[
        {img:require('./assets/dribbble.png'),url:''},
        {img:require('./assets/behance.png'),url:''},
        {img:require('./assets/instagram.png'),url:'https://www.instagram.com/uxtap/'},
      ],
      footerW:'',
      xsm:false,
      
    }),

    mounted () {
      this.onResize()
      
    },

    methods: {

        onScroll (e) {
        let top = e.target.scrollTop
        this.showBtn = top >= 3
          },
        onResize () {
            if (window.innerWidth >= 1904){ //xlarge ;

                this.viewport = 'xl'
                this.mew = 300
                this.bannerH = 400
                this.skillW = 1335
                this.toolW = 850
                this.drawer = false
                this.xsm = false

            }
            else if (window.innerWidth >= 1264 && window.innerWidth < 1904){ //large

                this.viewport = 'lg'  
                this.mew = 300
                this.bannerH = 400
                this.skillW = 1335
                this.toolW = 850
                this.drawer = false
                this.xsm = false

            }
            else if (window.innerWidth >= 960 && window.innerWidth < 1264){ //medium

                this.viewport = 'md' 
                this.mew = 300
                this.bannerH = 400
                this.skillW = 878
                this.toolW = 650
                this.drawer = false
                this.xsm = false

            }
            else if (window.innerWidth >= 600 && window.innerWidth < 960){ //small

                this.viewport = 'sm'  
                this.mew = 300
                this.bannerH = 400
                this.skillW = ''
                this.toolW = 450
                this.footerW = window.innerWidth*80/100
                this.xsm = true

              }
            else{ //xsmall

                this.viewport = 'xs'
                this.mew = window.innerWidth/4
                this.bannerH = window.innerHeight/3
                this.skillW = ''
                this.toolW = ''
                this.footerW = window.innerWidth*80/100
                this.xsm = true

            }
      
            
    },

    

    
    },
    
  }
</script>>
<style>

.html{
  scroll-behavior: smooth;
}

a{
    text-decoration: none;
}

.h100v{
  height: 100vh;
}
.v-application{
  font-family: 'Montserrat', sans-serif;
  
}
.stick{
  position:sticky !important;
}
.relative{
  position: relative;
}
.smw{
    border-radius: 60px !important;

    margin: 0;
    background: yellow;
    position: absolute;
    top: 50%;
    left: 50%;
    margin-right: -50%;
    transform: translate(-50%, -50%) }
.cdot{
  position: absolute;
  transform: translate(-100%)
}    
.v-menu__content {
    box-shadow: none;
}
.wcard{
  border-radius: 40px !important;
  height: 100%;
  width: 100%;
  box-shadow: 0px 30px 80px rgba(68, 0, 255, 0.116);
}

.cardNum{
  position: absolute;
  
}
.w50{
  max-width: 1335px;
}
.footer{
  background-color: #3F3D56 !important;
  border-top-left-radius: 40px !important;
  border-top-right-radius: 40px !important;
}

.toolb{
  border-bottom-left-radius: 40px !important;
  border-bottom-right-radius: 40px !important;
}


</style>
