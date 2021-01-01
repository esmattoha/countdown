<template>
  <div>
      <section class=" _sec">
      <div class="days">
        <h1>{{displayDays}}</h1>
        <div class="label text-sm absolute bottom-0">Days</div>
      </div>
      
      <div class="hours">
        <h1>{{displayHours}}</h1>
        <div class="label text-sm absolute bottom-0">Hours</div>
      </div>
      <div class="minutes">
        <h1>{{displayMinutes}}</h1>
        <div class="label text-sm absolute bottom-0">Minutes</div>
      </div>
      <div class="seconds">
         <h1>{{displaySeconds}}</h1>
         <div class="label text-sm absolute bottom-0">Seconds</div> 
      </div>
    </section>
    </div>
</template>

<script>
export default {
  data: () => ({
    displayDays: 0,
    displayHours: 0,
    displayMinutes: 0,
    displaySeconds: 0
  }),
  computed:{
    _seconds: () =>1000,
    _minutes: () =>{
      return this._seconds * 60 ;
    },
    _hours: () =>{
      return this._minutes * 60 ;
    },
    _days: () => {
      return this._hours * 24 ; 
    }
  },
  mounted(){
    this.showRemaining();
  },
  methods:{
    formateNum: (num) => (num < 10 ? "0" + num : num ),

    showRemaining(){
      const timer = setInterval(() => {
        const now = new Date();
        const end = new Date(2021 , 4, 22, 10, 10 ,10);
        const distance = end.getTime() - now.getTime();

        if(distance < 0 ){
          clearInterval(timer);
          return;
        }

        const days = Math.floor(distance/this._days);
        const hours = Math.floor((distance % this._days)/this._hours);
        const minutes = Math.floor((distance % this._hours)/this._minutes);
        const seconds = Math.floor((distance % this._minutes)/this._seconds);
        this.displayMinutes = this.formateNum(minutes);
        this.displaySeconds =this.formateNum(seconds);
        this.displayHours = this.formateNum(hours);
        this.displayDays =this.formateNum(days);
      }, 1000);
    }
  }
};
</script>

<style  scoped>

 ._sec{
   padding: auto;
   display: flex;
   text-align:center;;
 }
.days{
    width: 60px;
    border: 1px solid black;
    padding: 4px;
    margin: 5px;
  }
.hours{
    width: 60px;
    border: 1px solid black;
    padding: 4px;
    margin: 5px;
  }
.minutes{
    width: 60px;
    border: 1px solid black;
    padding: 4px;
    margin: 5px;
  }
.seconds{
    width: 60px;
    border: 1px solid black;
    padding: 4px;
    margin: 5px;
  }
</style>