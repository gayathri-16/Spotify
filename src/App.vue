<template>
  <div class=" h-screen flex-none" style="  background-color:rgb(10, 10, 10); height: 100vh;">
    <link rel="preconnect" href="https://fonts.gstatic.com">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.10.1/css/all.css">
       
     <div class="flex" style="height: 88vh;" >
     <div class="w-56 bg-black h-full flex-none" >

<div class="p-6" >
<img src="./assets/iconLogo.png" class="h-12" style="filter: brightness(1) invert(1); width:50px; height:50px; margin-bottom:-2.6rem;" alt="">
<span  class="title" style="font-size:30px; margin-left:4rem; font-weight:bold;">Spotify</span>
</div>

    <div  class="mx-3 mb-5">
    <button id= "btn" class="text-sm font-semibold " style="color:gray; margin-left:-5rem;font-size:16px; "><i class="fas fa-home"  id="home" style=" transform: scale(0.9);color:gray; margin-right:0.6rem;" ></i>  Home </button><br>
    <button id= "btn" class="text-sm font-semibold " style="color:gray; margin-left:-5rem; font-size:16px; "><i class="fas fa-search" style=" color:gray;margin-right:0.6rem;" ></i>  Search </button><br>
    <button id= "btn" class="text-sm font-semibold " style="color:gray; margin-left:-4rem; font-size:16px; "><i class="fas fa-bars" style=" color:gray;margin-right:0.6rem;" ></i>  YourLibrary </button><br>
    </div>

<div class="mx-5">
<h1 class="mb-5 text-xs text-lightest tracking-widest uppercase" style="color:gray; letter-spacing:2.5px;">Playlist</h1>
<button class="flex items-center justify-start opacity-75 hover:opacity-100 mb-2">
<img src="add new1.jpg" class="h-8 w-8 mr-3" style= "filter:  invert(0);"/>
<p class="text-sm text-white font-semibold">Create Playlist</p>
</button>
<button class="flex items-center justify-start opacity-75 hover:opacity-100 mb-2">
<img src="favourite.jpg" class="h-8 w-8 mr-3"/>
<p class="text-sm text-white font-semibold">Liked Songs</p>
</button>
<div class="h-px w-full bg-light my-3" style="margin-top:1rem; opacity-75; width:full; background-color:rgb(49, 47, 47);"></div>
</div>

<div class="mx-5">
  <div class="w-full h-10 overflow-y-scroll">
    <p  v-for="album in albums" :key="album" style="color:gray; font-size:16px; display:block; line-spacing:1px;" class=" opacity-75 hover:opacity-100">{{album.title}}</p>
    </div>
    <button class="flex items-center justify-start text-lightest hover:text-white py-2">
     <i class="fas fa-arrow-circle-down " style="color:white;filter:invert(0);margin:8px;padding:2px;"></i>
      <p class="text-sm font-semibold" id="glow" style="font-size:15px; color:gray; ">Install App</p>
    </button>
</div>
<div class="relative pt-6 ">
  <div class="w-full h-full flex justify-end items-start opacity-0 hover:opacity-100 p-2  absolute">
    <div class=" ">
     <i class="fas fa-chevron-circle-down text-black" ></i>
    </div>
  </div>
      <img src="playing.jpg"  />

</div>
</div>

<div class="w-full h-full relative overflow-y-scroll">
<!-- header-->
  <div class="w-full sticky top-0 py-4 px-6 flex items-center justify-between bg-dark">
    <div class="flex items-center">
      <button class="rounded-full   w-8 h-8  mr-3">
        <i class="fas fa-angle-left text-3xl" style="filter:invert(1); text-white;"></i>
      </button>
       <button class="rounded-full w-8 h-8 text-white mr-3">
        <i class="fas fa-angle-right text-3xl" ></i>
      </button>
    </div>
    <div class="relative">
      <button @click="showDropdown = true" class=" focus:outline-none rounded-full py-1 px-2 flex items-center" style="background-color:rgb(49, 47, 47);">
        <img src="mickey mouse.jpg" class= "rounded-full h-6 w-6 mr-2" />
        <p class="text-white  font-semibold text-xs mr-3 "> Stephnie Dietz</p>
        <i v-if="showDropdown === false" class="fas fa-caret-down text-white" ></i>
        <i v-if="showDropdown === true" class="fas fa-caret-up text-white" ></i>
      </button>
      <div v-if="showDropdown === true" class="absolute rounded mt-1 w-full " style="background-color:rgb(49, 47, 47)">
        <button @click="showDropdown = false" class=" focus:outline-none w-full text-sm text-lightest hover:text-white py-2 border-b border-white opacity-75 hover:opacity-100" >Account</button>
        <button @click="showDropdown = false" class=" focus:outline-none w-full text-sm text-lightest hover:text-white py-2  opacity-75 hover:opacity-100" >Log Out</button>
      </div>
    </div>
  </div>

  <!-- cards -->
  <div class="px-6 py-3">
<div class="flex  item-center justify-between">
  <h1 class=" pl-2 text-2xl font-semibold text-white tracking-wider hover:underline"> Recently Played</h1>
  <h2 class=" pr-4 pt-4 text-xs text-lightest uppercase tracking-wider hover:underline mb-3" style="color:rgb(150,147,147);">See All</h2>
 </div>
  <div class="w-full flex flex-wrap">
    <div class="p-2 w-48 relative"> 
      <div class="absolute w-full h-full flex items-end justify-end p-8 opacity-0 hover:opacity-100">
        <div style=" background:green;"  class=" rounded-full h-10 w-10 flex items-center justify-center" >
          <i class="fas fa-play text-white text-2xl">  
          </i>
        </div>
      </div>

<div id="dropdown">       
 <div class="p-6 mx-3 rounded-lg shadow-md relative opacity-75 hover:opacity-100" style=" width:150px; height:200px; background-color:rgb(150,147,147);"> <img  src='allu.jpg' alt=""> 
     <span> <button class="absolute" id="song-list" style=" width:120px;height:50px; margin-left:-0.5rem; margin-top:1rem; transparent:(-50%, -50%);" v-for="song in songs" :key="song.src" @click="play(song)" :class="(song.src == current.src) ? 'song playing' :'song'" >
      <h1 style="color:white; focus:outline-none; font-size:16px;">Butta Bomma</h1><span style="color:black; font-size:12px; margin-top:-1.5rem; ">Dj santhosh</span>
   </button></span>
 </div>

  <div class="p-6  rounded-lg shadow-md relative opacity-75 hover:opacity-100" style=" width:150px; height:200px; margin-left:12rem;  margin-top:-12.5rem; background-color:rgb(150,147,147);">    <img src='kadhaipomma.jpg' alt="">
     <span><button class="absolute" id="song-list" style=" width:120px;height:50px; margin-left:-0.5rem; margin-top:1rem; transparent:(-50%, -50%);" v-for="song in songs" :key="song.src" @click="play(song)" :class="(song.src == current.src) ? 'song playing' :'song'" >
          <h1 style="color:white; focus:outline-none; font-size:16px;">Kadhaipomma</h1><span style="color:black; font-size:12px; margin-top:-1.5rem; ">Leon James,Sid Sriram </span>
    </button></span> 
  </div>

    <div class="p-6 ml-3 rounded-lg shadow-md  relative opacity-75 hover:opacity-100" style=" width:150px; height:200px; margin-left:24rem; margin-top:-12.5rem; background-color:rgb(150,147,147);">    <img src='komali.jpg' alt="">
        <span> <button class="absolute" id="song-list" style=" width:120px;height:50px; margin-left:-0.5rem; margin-top:1rem; transparent:(-50%, -50%);" v-for="song in songs" :key="song.src" @click="play(song)" :class="(song.src == current.src) ? 'song playing' :'song'" >
           <h1 style="color:white; focus:outline-none; font-size:16px;">paisa Note</h1><span style="color:black; font-size:12px; margin-top:-1.5rem; ">Hip-Hop Aadhi </span>
         </button></span> 
    </div>

  <div class="p-6 ml-3 rounded-lg shadow-md relative opacity-75 hover:opacity-100 " style=" width:150px; height:200px; margin-left:36rem; margin-top:-12.5rem; background-color:rgb(150,147,147);">    <img  src='remo.jpg' alt="">
        <span> <button class="absolute" id="song-list" style=" width:120px;height:50px; margin-left:-0.5rem; margin-top:1rem; transparent:(-50%, -50%);" v-for="song in songs" :key="song.src" @click="play(song)" :class="(song.src == current.src) ? 'song playing' :'song'" >
          <h1 style="color:white; focus:outline-none; font-size:16px;">Senjitaley</h1><span style="color:black; font-size:12px; margin-top:-1.5rem; ">Aniruth ravichandran </span>
         </button> </span> 
 </div>
     
    <div class="p-6 ml-3 rounded-lg shadow-md relative opacity-75 hover:opacity-100 " style=" width:150px; height:200px; margin-left:48rem; margin-top:-12.5rem; background-color:rgb(150,147,147);">    <img src='Master.jpg' alt="">
     <span><button class="absolute" id="song-list" style=" width:120px;height:50px; margin-left:-0.5rem; margin-top:1rem; transparent:(-50%, -50%);" v-for="song in songs" :key="song.src" @click="play(song)" :class="(song.src == current.src) ? 'song playing' :'song'" >
          <h1 style="color:white; focus:outline-none; font-size:16px;">Kutty Story</h1><span style="color:black; font-size:12px; margin-top:-1.5rem; ">Aniruth </span>
    </button></span> 
  </div>

  <div class="p-6 ml-3 rounded-lg shadow-md relative opacity-75 hover:opacity-100 " style=" width:150px; height:200px; margin-left:60rem; margin-top:-12.5rem; background-color:rgb(150,147,147);">    <img src='OMK.jpg' alt="">
     <span><button class="absolute" id="song-list" style=" width:120px;height:50px; margin-left:-0.5rem; margin-top:1rem; transparent:(-50%, -50%);" v-for="song in songs" :key="song.src" @click="play(song)" :class="(song.src == current.src) ? 'song playing' :'song'" >
          <h1 style="color:white; focus:outline-none; font-size:16px;">Marapadhillai </h1><span style="color:black; font-size:12px; margin-top:-1.5rem; ">Sid Sriram </span>
         </button></span> 
  </div>
      
          </div>
       </div>
   </div>
</div>

  <div class="px-6 py-5">
    <div class="pl-2">
     <h1 class="  text-2xl font-semibold text-white tracking-wider hover:underline"> Made for Stepnie</h1>
     <h2 class="  text-sm" style="color:rgb(150,147,147);">Get better recommondation that more you listen</h2>
    </div>
<div class="w-full flex flex-wrap py-5">
   <div class="absolute w-full h-full flex items-end justify-end p-8 opacity-0 hover:opacity-100">
      <div class=" rounded-full h-10 w-10 flex items-center justify-center" style="background-color:green;">
          <i class="fas fa-play text-white text-2xl"></i>
        </div>
      </div>
   
<div id="dropdown" >
         
    <div class="p-6 mx-3 rounded-lg shadow-md relative opacity-75 hover:opacity-100" style=" width:150px; height:200px; background-color:rgb(150,147,147);"> <img  src='allu.jpg' alt=""> 
     <span> <button class="absolute" id="song-list" style=" width:120px;height:50px; margin-left:-0.5rem; margin-top:1rem; transparent:(-50%, -50%);" v-for="song in songs" :key="song.src" @click="play(song)" :class="(song.src == current.src) ? 'song playing' :'song'" >
      <h1 style="color:white; focus:outline-none; font-size:16px;">Butta Bomma</h1><span style="color:black; font-size:12px; margin-top:-1.5rem; ">Dj santhosh</span>
   </button></span>
 </div>

  <div class="p-6  rounded-lg shadow-md relative opacity-75 hover:opacity-100" style=" width:150px; height:200px; margin-left:12rem;  margin-top:-12.5rem; background-color:rgb(150,147,147);">    <img src='kadhaipomma.jpg' alt="">
     <span><button class="absolute" id="song-list" style=" width:120px;height:50px; margin-left:-0.5rem; margin-top:1rem; transparent:(-50%, -50%);" v-for="song in songs" :key="song.src" @click="play(song)" :class="(song.src == current.src) ? 'song playing' :'song'" >
          <h1 style="color:white; focus:outline-none; font-size:16px;">Kadhaipomma</h1><span style="color:black; font-size:12px; margin-top:-1.5rem; ">Leon James,Sid Sriram </span>
    </button></span> 
  </div>

    <div class="p-6 ml-3 rounded-lg shadow-md  relative opacity-75 hover:opacity-100" style=" width:150px; height:200px; margin-left:24rem; margin-top:-12.5rem; background-color:rgb(150,147,147);">    <img src='komali.jpg' alt="">
        <span> <button class="absolute" id="song-list" style=" width:120px;height:50px; margin-left:-0.5rem; margin-top:1rem; transparent:(-50%, -50%);" v-for="song in songs" :key="song.src" @click="play(song)" :class="(song.src == current.src) ? 'song playing' :'song'" >
           <h1 style="color:white; focus:outline-none; font-size:16px;">paisa Note</h1><span style="color:black; font-size:12px; margin-top:-1.5rem; ">Hip-Hop Aadhi </span>
         </button></span> 
    </div>

  <div class="p-6 ml-3 rounded-lg shadow-md relative opacity-75 hover:opacity-100 " style=" width:150px; height:200px; margin-left:36rem; margin-top:-12.5rem; background-color:rgb(150,147,147);">    <img  src='remo.jpg' alt="">
        <span> <button class="absolute" id="song-list" style=" width:120px;height:50px; margin-left:-0.5rem; margin-top:1rem; transparent:(-50%, -50%);" v-for="song in songs" :key="song.src" @click="play(song)" :class="(song.src == current.src) ? 'song playing' :'song'" >
          <h1 style="color:white; focus:outline-none; font-size:16px;">Senjitaley</h1><span style="color:black; font-size:12px; margin-top:-1.5rem; ">Aniruth ravichandran </span>
         </button> </span> 
 </div>
     
    <div class="p-6 ml-3 rounded-lg shadow-md relative opacity-75 hover:opacity-100 " style=" width:150px; height:200px; margin-left:48rem; margin-top:-12.5rem; background-color:rgb(150,147,147);">    <img src='Master.jpg' alt="">
     <span><button class="absolute" id="song-list" style=" width:120px;height:50px; margin-left:-0.5rem; margin-top:1rem; transparent:(-50%, -50%);" v-for="song in songs" :key="song.src" @click="play(song)" :class="(song.src == current.src) ? 'song playing' :'song'" >
          <h1 style="color:white; focus:outline-none; font-size:16px;">Kutty Story</h1><span style="color:black; font-size:12px; margin-top:-1.5rem; ">Aniruth </span>
    </button></span> 
  </div>

  <div class="p-6 ml-3 rounded-lg shadow-md relative opacity-75 hover:opacity-100 " style=" width:150px; height:200px; margin-left:60rem; margin-top:-12.5rem; background-color:rgb(150,147,147);">    <img src='OMK.jpg' alt="">
     <span><button class="absolute" id="song-list" style=" width:120px;height:50px; margin-left:-0.5rem; margin-top:1rem; transparent:(-50%, -50%);" v-for="song in songs" :key="song.src" @click="play(song)" :class="(song.src == current.src) ? 'song playing' :'song'" >
          <h1 style="color:white; focus:outline-none; font-size:16px;">Marapadhillai </h1><span style="color:black; font-size:12px; margin-top:-1.5rem; ">Sid Sriram </span>
         </button></span> 
  </div>
       </div>
     </div>
  </div>
  
  </div>
</div>
    <div class="w-full flex items-center justify-between px-3 border-dark " style=" background-color:rgba(30,30,30,0.1);height:12vh">
      <div class="flex items-center">
        <div>
          <h1 class="mb-1 text-sm text-white tracking-wide"> Summer in the City-Remastered</h1>
          <h2 class="text-xs tracking-wide" style="color:rgb(150, 147, 147);"> The Lovin' Spoonfull</h2>
        </div>
        <i class="fas fa-heart text-base  mx-4" style="color:green;"></i>
        <i class="fas fa-sticky-note text-base" style="color:rgb(150, 147, 147);"> </i>
      </div>
      <div class="flex flex-col justify-center w-2/4 items-center">
        <div class=" flex items-center">
          
          <button class="  text-white opacity-20 hover:opacity-100 mx-5" ><i class="fas fa-random text-lg"></i></button> 
          <button class="  text-white opacity-20 hover:opacity-100 mx-3" ><i class="fas fa-step-backward text-lg" id="prev" title="Previous" @click="prev"></i></button> 
          <button class=" mx-5 rounded-full  h-8 w-8 flex items-center justify-center  border-lightest  border text-white opacity-20 hover:opacity-100"><i v-if="!isPlaying" @click="play" class="fas fa-play"></i>
          <i v-else @click="pause" class="fas fa-pause"></i></button>
          <button class=" text-base text-white opacity-20 hover:opacity-100 mx-3 " ><i class=" text-lg fas fa-step-forward" id="next" title="Next" @click="next"></i></button> 
          <button class="  text-white opacity-20 hover:opacity-100  mx-5"><i class=" text-lg fas fa-redo-alt" id="repeat" title="Repeat" @click="redo"></i></button>
        </div>
        <div class="w-3/4 flex items-center justify-center mt-3">
      <p class="text-xs text-white mr-1">0:28</p>
          <div class="w-full h-1 rounded-full  flex items-center" style="background-color:black;">
          <div class="h-1 rounded-full " style="width:18%; background-color:green;">
          </div>
        <div class="h-3 w-3 bg-white rounded-full -ml-1 " style=" box-shadow: 0 1rem 2rem 0.2rem rgba(0, 0, 0, 0.4);">
      </div>
     </div>
       <p class="text-xs text-white ml-1 " >2:40</p>
          </div>
        </div>
      
      <div class="flex item-center w-1/4 justify-end">
        <i class="fad fa-user-music mx-3 text-lightest hover:text-white" style="color:rgb(150, 147, 147);"></i>
           <i class="fas fa-desktop mx-3 text-lightest hover:text-white" style=" color:rgb(150,147,147);"></i>
        <i class="fas fa-volume-up text-lightest hover:text-white" style="color:rgb(150, 147, 147);"></i>
        <div class="w-20 ml-1 bg-lightest rounded-full h-1"></div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  album:'',
  data() {
    return {
      current:{},
      index: 0,
      isPlaying: false,
      
      albums:[
{'title':'drive'},
{'title':'zhu'},
{'title':'All New Indie'},
{'title':'Mellow'},
{'title':'Classic Road Trip Songs'},
{'title':'Lana Del Rey Radio'}
      ],
      showDropdown: false,

     songs:[
        {src: require('./assets/kutty story.mp3')},
        {src: require('./assets/kadhaipomma.mp3')},
        {src: require('./assets/Paisa Note.mp3')},
        {src: require('./assets/Senjitaley.mp3')},
        {src: require('./assets/song.mp3')},
        {src: require('./assets/allu arjun.mp3')}
       ],
      
       player:new Audio(),
    };
  },
  methods:{
     play(song){
         
          if(typeof song.src != "undefined"){
            this.current = song;
            this.player.src = this.current.src;
          
          }
          
          this.player.play();
          this.isPlaying = true;
          
       },
        pause(){
         this.player.pause();
         this.isPlaying = false;
       },
   next(){
         this.index++;
         if(this.index > this.songs.length - 1){
           this.index = 0;
         }

         this.current = this.songs[this.index];
         this.play(this.current);
       },
       prev() {
         this.index--;
         if(this.index < 0 ){
           this.index = this.songs.length - 1;
         }

         this.current = this.songs[this.index];
         this.play(this.current);
       },

  created(){
    this.current = this.songs[this.index];
    this.player.src = this.current.src;
  }
  }

}
</script>

<style>

#btn{
   width:250px;
  height:40px; 
  margin-left:-4rem;  
 
  
}
#btn:hover{
  background-color:rgb(48, 48, 48);
  border-radius: 5px;
  
  
color:white;
}
#text:hover{
  color:rgb(49, 47, 47);
}
::-webkit-scrollbar{
  width:8px;

}
::-webkit-scrollbar-thumb{
  background-image:linear-gradient(transparent, #454645);
  border-radius:6px;
  
}
::-webkit-scrollbar-thumb:hover{
   background-image:linear-gradient(transparent, #ff004c);
   filter:blur(30px);
}
.title{
  color:transparent;
    
  transform: translate(-50%,-50%);
 
  background-image: linear-gradient(
    to right,
    #462523  0,
    #cb9b51  22%,
    #f6e27a  45%,
    #f6f2c0  50%,
    #f6e27a  55%,
     #cb9b51  78%,
     #462523  100%
  );
  -webkit-background-clip:text;
  }
   
    #dropdown{
      width:700px;
      height:200px;
   }
    
</style>
