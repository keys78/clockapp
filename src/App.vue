<template>

  <div id="heroic" class="w-full h-screen">
    <div class="py-12 lg:px-24 px-8">
        <div class="flex items-start gap-6 h-10 lg:w-7/12 w-full ">
          <div class="lg:w-7/12 sm:w-10/12 w-full animate__animated animate__slideInLeft  animate__faster">
            <p class="text-white" v-if="quotesContent"> {{ quotesContent }} </p>
            <p class="text-white font-bold italic mt-4" v-if="quotesAuthor">- {{ quotesAuthor }}</p>
          </div>
          <div class="lg:w-3/12 sm:w-5/12 w-2/12">
            <button class="focus:outline-none" @click="refreshQuotes"><img id="refresh-icon" src="./assets/desktop/icon-refresh.svg"/></button>
          </div>
        </div>

        <div class="pt-80">
          <div class="flex items-center gap-4">
              <!-- <div v-if="galaxyIcon"> {{ galaxyIcon }}</div> -->
              <!-- <img :src="galaxyIcon"/> -->
              <img id="sun" src="./assets/desktop/icon-sun.svg"/>
              <img id="moon" src="./assets/desktop/icon-moon.svg"/>
              <h1 v-if="greetings" class="tracking-wider md:text-3xl sm:text-2xl text-base text-white"> {{ greetings }}, IT'S CURRENTLY </h1>
          </div>
          <h1 v-if="timestamp" class="md:text-9xl sm:text-8xl text-6xl py-4 text-white font-bold"> {{ timestamp }} <span v-if="abbreviation" class="text-xl font-medium"> {{ abbreviation }} </span></h1>

          <h2 class="md:text-2xl sm:text-xl text-base font-semibold text-white uppercase tracking-widest" v-if="timezone">IN {{ timezone }} </h2>
        </div>
         <button @click="openNav" class="absolute sm:bottom-20 bottom-8 sm:right-24 right-12 text-black bg-white py-1 myhov px-4 flex items-center gap-3 focus:outline-none cursor-pointer rounded-2xl" ><span>More</span> <img  id="showmore-Btn" class="w-7" src="./assets/desktop/icon-arrow-up.svg"/></button>
    </div>

       
        <div id="myBottomNav" class="bottomNav h-2/4 bg-black opacity-90 lg:px-24 px-8 ">

          <button @click="closeNav"  id="showmore-Btn" class="absolute sm:bottom-20 bottom-8 sm:right-24 right-12 bg-white text-black py-1 myhov px-4 flex items-center gap-3 focus:outline-none cursor-pointer rounded-2xl"><span>Lesss </span> <img  class="w-7  iconio" src="./assets/desktop/icon-arrow-up.svg"/></button>

          <div class="flex justify-between items-start">

              <div >
                <div class="py-16 lg:w-6/12 sm:w-8/12 w-full">
                  <p class="sm:text-base text-xs uppercase tracking-wide text-gray-200">Current Timezone</p>
                  <p v-if="currentTimezone" class="uppercase lg:text-5xl sm:text-4xl text-2xl font-semibold text-gray-200">{{ currentTimezone }}</p>
                </div>
                
                <div>
                  <p class="sm:text-base text-xs uppercase tracking-wide text-gray-200">Day of the year</p>
                  <p v-if="dayofyear" class="uppercase lg:text-5xl sm:text-4xl text-2xl font-semibold text-gray-200">{{ dayofyear }}</p>
                </div>
              </div>

              <div class="sm:border-l-2  border-none border-gray-200 w-6/12">
                  <div class="py-16 pl-8">
                    <p class="sm:text-base text-xs uppercase tracking-wide text-gray-200">Day of the week</p>
                    <p v-if="dayofweek" class="uppercase lg:text-5xl sm:text-4xl text-2xl font-semibold text-gray-200">{{ dayofweek }}</p>
                  </div>

                  <div class="pl-8">
                    <p class="sm:text-base text-xs uppercase tracking-wide text-gray-200">week number</p>
                    <p v-if="weekNumber" class="uppercase lg:text-5xl sm:text-4xl text-2xl font-semibold text-gray-200">{{ weekNumber }}</p>
                  </div>
              </div>

          </div>

        </div>

  </div>
</template>

// <script>
//   import Sun from "./assets/desktop/icon-sun.svg"
//   import Moon from "./assets/desktop/icon-moon.svg"
export default {
  
  name: 'App',
  components: {
  
  },
  data() {
    return {
      quotesContent:'The universe is transformation; our life is what our thoughts make it.',
      quotesAuthor: 'Em_codes',
      greetings:'',
      timestamp:'',
      abbreviation:'',
      timezone:'',
      // galaxyIcon:''
      currentTimezone:'',
      dayofyear:'',
      dayofweek:'',
      weekNumber:'',
     
    }
  },
  
  methods: {

     openNav() {
                document.getElementById("myBottomNav").style.height = "50%";
                document.getElementById("heroic").style.marginBottom = "350px";
                document.body.style.background = "black"
              },

              closeNav() {
                document.getElementById("myBottomNav").style.height = "0";
                document.getElementById("heroic").style.marginBottom= "0";
              },






      refreshQuotes() {
         fetch('https://api.quotable.io/random')
            .then(res => {
              
                return res.json();
                })
            .then(data => {
            console.log(data)
            this.quotesContent = data.content
            this.quotesAuthor = data.author
            
            })
         
      },

       getNow: function() {
                    const today = new Date();
                    const time = today.getHours() + ":" + today.getMinutes() + ":" + today.getSeconds();
                    const currentTime = time;
                    this.timestamp = currentTime;

                    const myHour = today.getHours()
                    myHour >= 12 ? document.getElementById('heroic').style.backgroundImage = "url('https://images.pexels.com/photos/920534/pexels-photo-920534.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940')" : document.getElementById('heroic').style.backgroundImage = "url('https://images.pexels.com/photos/1024981/pexels-photo-1024981.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940')"
                    myHour >= 12 ? this.greetings = "GOOD EVENING" : this.greetings = "GOOD MORNING";
                    if(myHour >= 12){
                       document.getElementById('sun').style.display = 'none';
                       document.getElementById('moon').style.display = 'block';
                    }else{
                        document.getElementById('sun').style.display = 'block';
                       document.getElementById('moon').style.display = 'none';
                    }
                }

  },

      created() {
                    setInterval(this.getNow, 1000);
                },
                  
      mounted() 
      {
        fetch('https://worldtimeapi.org/api/ip')
                .then(res => {
                    return res.json();
                    })
                .then(data => {
                console.log(data)
                this.abbreviation = data.abbreviation
                this.currentTimezone = data.timezone
                this.timezone = data.timezone
                this.dayofyear = data.day_of_year
                this.dayofweek = data.day_of_week
                this.weekNumber = data.week_number
                })
       
               
          
      },
  
  





}
</script>

<style>

 *{
  padding: 0;
  margin:0;
}
#refresh-icon:hover{
  transform: rotate(360deg);
  transition: 1.2s ease-in-out;
}


/* POPUP */
#showmore-Btn:hover .iconio{
   transform: rotate(180deg);
   transition: 0.3s ease-in-out;
}
.iconio{
    transition: 0.3s ease-in-out;
}


.bottomNav {
  width:100vw;
  height: 0;
  position: fixed;
  bottom: 0;
  z-index: 1;
  overflow: hidden;
  transition: 0.5s;
}

.myhov:hover{
  transform: scale(1.1);
  transition: 0.3s ease-in-out;
}
.myhov{
  transition: 0.3s ease-in-out;
}

</style>
