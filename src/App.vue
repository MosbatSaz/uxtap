<template>
  <v-app class="d-flex justify-center">

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

  <!-- Toolbar -->
  <v-card flat  class="ma-0 pa-0 transparent">
    
 
     <v-toolbar flat :height="(viewport == 'xs')?50:100" class="mon ma-0 pa-0">

      <img :class="`${(viewport == 'xs') ? 'ml-3':'ml-12'} mt-6`" :height="(viewport == 'xs') ? '50':'70'"  src="./assets/ux tap logo.png"/>

      <v-spacer></v-spacer>
  
      <v-btn 
      height="80"
      :ripple="true"  
      v-for="(item,i) in items" :key="i" 
      :class="`${(i == 4)?'mr-12 ml-12' : 'mx-3'} deep-purple--text text--darken-3  transparent text-capitalize  mt-6 hidden-sm-and-down`" 
      text>
      <v-row class="pa-0" justify="center" align="center">
        <v-col class=" ma-0 pa-0 mb-2 grey--text text--darken-3" cols="12"><span>{{item.title}}</span></v-col>
       <v-col class="ma-0 pa-0" cols="12"><v-icon color="deep-purple darken-3">{{item.icon}}</v-icon></v-col>
      </v-row>
      </v-btn>
      

      <v-app-bar-nav-icon 
      x-large
      class="transparent grey--text text--darken-3 mr-1 mt-6 hidden-md-and-up" >
      </v-app-bar-nav-icon>
      
      </v-toolbar>
  </v-card>
  <!-- Navigation Drawr -->


  <!-- Introduce Me -->
  <v-card flat class=" my-10">
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
         <v-btn class=" text-capitalize  px-1 deep-purple lighten-4 deep-purple--text elevation-1"> Know Me Better</v-btn></v-card >

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
            <v-btn width="200" height="75" class="smw">
              <img height="20" class="mr-1" src="./assets/my works icon.png" />
              <span class="ml-1 mon text-capitalize">See My Works</span>
            </v-btn>
          </v-card>
        </v-parallax>
        
    </v-card>
  

  <!-- Know Me Better -->

    <v-card flat class="text-center mon mt-4 hidden-xs-only">
      <v-row class="pa-0 ma-0" justify="center" align="center">
        <v-col class=" ma-0 pa-0 mb-n1 deep-purple--text text--darken-3" cols="12"><span>Know Me Better</span></v-col>
        <v-col class="ma-0 pa-0" cols="12"><v-icon color="deep-purple darken-3" large>mdi-chevron-down</v-icon></v-col>
      </v-row>
    </v-card>


  <!-- My Works -->
  <v-card flat class="ma-0 pa-0  mt-12" height="">

    <!-- <v-img  src="./assets/Back Dot.png"> -->
    
    <div class="text-center my-12 display-2 font-weight-bold">
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
    <div class="text-center my-12 display-2 font-weight-bold">
    My Skills
    </div>

    <v-card flat class="d-flex justify-center transparent">
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
  <!-- Footer -->



  </v-app>
</template>



<script>
 
  export default {

    data: () => ({
      viewport: '',
      items:[
        {title:'My Works',icon:'mdi-collage'},
        {title:'How I Work',icon:'mdi-cellphone-link'},
        {title:'My Skills',icon:'mdi-cards'},
        {title:'Tools I Use',icon:'mdi-tools'},
        {title:'contact me',icon:'mdi-auto-fix'}
      ],
      mew:0,
      bannerH:0,
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
    }),

    mounted () {
      this.onResize()
    },

    methods: {
      // 878 : 1335"
        onResize () {
            if (window.innerWidth >= 1904){ //xlarge ;

                this.viewport = 'xl'
                this.mew = 300
                this.bannerH = 400
                this.skillW = 1335

            }
            else if (window.innerWidth >= 1264 && window.innerWidth < 1904){ //large

                this.viewport = 'lg'  
                this.mew = 300
                this.bannerH = 400
                this.skillW = 1335

            }
            else if (window.innerWidth >= 960 && window.innerWidth < 1264){ //medium

                this.viewport = 'md' 
                this.mew = 300
                this.bannerH = 400
                this.skillW = 878

            }
            else if (window.innerWidth >= 600 && window.innerWidth < 960){ //small

                this.viewport = 'sm'  
                this.mew = 300
                this.bannerH = 400
                this.skillW = ''

              }
            else{ //xsmall

                this.viewport = 'xs'
                this.mew = window.innerWidth/4
                this.bannerH = window.innerHeight/3
                this.skillW = ''

            }
    },
    },
    
  }
</script>>
<style>

.mon{
  font-family: 'Montserrat', sans-serif;
}
.relative{
  position: relative;
}
.smw{
    border-radius: 50px !important;

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
</style>
