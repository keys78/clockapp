<template>


  <div>
    <Showmore/>
  </div>






  <!-- <div id="heroic" class="w-full md:h-screen h-auto p-12" >
    <div class="">
      <p class="text-white" v-if="quotesContent"> {{ quotesContent }} </p>
      <p class="text-white" v-if="quotesAuthor"> {{ quotesAuthor }}</p>
      <button class="focus:outline-none" @click="refreshQuotes"><img id="refresh-icon" src="./assets/desktop/icon-refresh.svg"/></button>
    </div>

    <div class="pt-96">
      <div>
        <svg width="24" height="24" xmlns="http://www.w3.org/2000/svg"><path d="M11.78 19.417c.594 0 1.083.449 1.146 1.026l.006.125v1.842a1.152 1.152 0 01-2.296.125l-.007-.125v-1.842c0-.636.516-1.151 1.152-1.151zM6.382 17.18a1.15 1.15 0 01.09 1.527l-.09.1-1.302 1.303a1.152 1.152 0 01-1.718-1.528l.09-.1 1.302-1.302a1.15 1.15 0 011.628 0zm12.427 0l1.303 1.303a1.15 1.15 0 11-1.628 1.627L17.18 18.81a1.15 1.15 0 111.628-1.628zM11.781 5.879a5.908 5.908 0 015.901 5.902 5.908 5.908 0 01-5.901 5.902 5.908 5.908 0 01-5.902-5.902 5.908 5.908 0 015.902-5.902zm10.63 4.75a1.151 1.151 0 110 2.303h-1.843a1.151 1.151 0 110-2.303h1.842zm-19.418 0a1.151 1.151 0 01.126 2.296l-.125.007H1.15a1.151 1.151 0 01-.125-2.296l.125-.007h1.842zm1.985-7.268l.1.09 1.303 1.302a1.151 1.151 0 01-1.528 1.718l-.1-.09L3.45 5.08A1.15 1.15 0 014.978 3.36zm15.133.09c.45.449.45 1.178 0 1.628L18.808 6.38a1.151 1.151 0 11-1.628-1.628l1.303-1.303c.449-.449 1.178-.449 1.628 0zM11.781 0c.636 0 1.151.515 1.151 1.151v1.843a1.152 1.152 0 01-2.303 0V1.15C10.63.515 11.145 0 11.781 0z" fill="#FFF" fill-rule="nonzero"/></svg>
      </div>
      <h1 v-if="greetings" class="text-3xl text-white"> {{ greetings }}, IT'S CURRENTLY </h1>
      <h1 v-if="timestamp" class="text-9xl text-white font-bold"> {{ timestamp }} <span v-if="abbreviation" class="text-base"> {{ abbreviation }} </span></h1>

      <div class="flex justify-between">
      <h2 class="text-2xl text-bold text-white uppercase" v-if="timezone">IN {{ timezone }} </h2>
        <button class="focus:outline-none" @click="showMoreLess"><img id="refresh-icon" src="./assets/desktop/icon-arrow-up.svg"/></button>
      </div>
    </div>


     -->
</template>

<script>
import Showmore from './components/Showmore.vue'

export default {
  name: 'App',
  components: {
    Showmore
  },
  data() {
    return {
      quotesContent:'',
      quotesAuthor: '',
      greetings:'',
      timestamp:'',
      abbreviation:'',
      timezone:'',
    }
  },
  
  methods: {
      refreshQuotes() {
          this.quotesContent.length > 0 ? document.getElementById('refresh-icon').style.animation = "rotation 1s linear" : document.getElementById('refresh-icon').style.animation = "rotation 1s linear"
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
                    myHour >= 12 ? this.greetings = "GOOD EVENING" : this.greetings = "GOOD MORNING"
                }

  },

      created() {
                    setInterval(this.getNow, 1000);
                },
                  
      mounted() 
      {
        fetch('http://worldtimeapi.org/api/ip')
                .then(res => {
                    return res.json();
                    })
                .then(data => {
                console.log(data.abbreviation)
                // this.greetings = 'GOOD MORNINING, ITS CURRENTLY'
                this.abbreviation = data.abbreviation
                this.timezone = data.timezone
                this.currenttime = data.datetime
              
                })
          // this.timestamp.value >= 12 ? document.getElementById('heroic').style.background = 'red' : document.getElementById('heroic').style.backgroundImage = 'green'
          
      },
  
  





}
</script>

<style>

 *{
  padding: 0;
  margin:0;
}

.hero-bg{
   background-image: url('https://images.pexels.com/photos/1024981/pexels-photo-1024981.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940');
  background-repeat: no-repeat;
  background-position: cover;
  width:100%;
}



@-webkit-keyframes rotation {
		from {
				-webkit-transform: rotate(0deg);
		}
		to {
				-webkit-transform: rotate(359deg);
		}
}
@keyframes rotation {
		from {
				-webkit-transform: rotate(0deg);
		}
		to {
				-webkit-transform: rotate(359deg);
		}
}

/* .heroic{
  background-image: url('https://images.pexels.com/photos/920534/pexels-photo-920534.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940');
  background-repeat: no-repeat;
  background-position: cover;
  width:100%;
} */

</style>
