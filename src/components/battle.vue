<template>
  <div>
    <v-button @click="Start()" class="btn">
      <img src="../assets/a.png" width="250" height="200" />
      
    </v-button>
    <br />
    <button v-bind:disabled="end" @click="randomenergy()" class="btn btn-#42b983"><img src="../assets/a2.png" width="80" height="80" /> {{Label}}</button>
    <button v-bind:disabled="end" @click="randomSpenergy()" class="btn btn"><img src="../assets/z.png" width="100" height="80" />{{Label}}</button>

    <div class="row text-light ">
      <div class="col-sm">
        <p>{{randomPlayer}}</p>
        <p>HP : {{hp1}}</p>
        <p>
          <img v-bind:style="{width : hp1 + 'px'}" :src="healthbar1" alt height="25px" />
        </p>
        <img :src="imagePlayer" :height="hp1" />
      </div>

      <div class="col-sm text-danger">
        <h1 v-if="hp1 <= 0 & hp2 <=0">
          <br />
          <img src="https://cdn.discordapp.com/attachments/392353546332405763/748200974153154640/235-2359549_street-fighter-ko-png-ko-street-fighter-png.png">
          DRAW
        </h1>
        <h1 v-else-if="hp2 <= 0 ">
          <br />
          <img src="https://cdn.discordapp.com/attachments/392353546332405763/748200974153154640/235-2359549_street-fighter-ko-png-ko-street-fighter-png.png">
          {{randomPlayer}} WIN
        </h1>
        <h1 v-else-if="hp1 <= 0 ">
          <br />
          <img src="../assets/P.png" >
          {{randomMonster}} WIN
        </h1>
        <br /><br /><br />
        <p v-if="hp1!=0 & hp2!=0">
          <img
            src="https://cdn.discordapp.com/attachments/748568284374499452/748852439603478599/t.gif"
          />
        </p>
      </div>

      <div class="col-sm">
        <p>{{randomMonster}}</p>
        <p>HP : {{hp2}}</p>
        <p>
          <img v-bind:style="{width: hp2 + 'px'}" :src="healthbar2" alt height="25px" />
        </p>
        <img :src="imageMonster" :height="hp2" />
        
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      randomPlayer: "",
      randomMonster: "",
      randomPlayerAttack: "",
      randomMonsterAttack: "",
      chosenNumber1:"",
      chosenNumber2:"",
      imagePlayer: "",
      imageMonster: "",
      hp1: "1",
      hp2: "1",
      end: false,
      healthbar1:
        "https://cdn.discordapp.com/attachments/748568284374499452/748851535403810856/mgg.png",
      healthbar2:
        "https://cdn.discordapp.com/attachments/748568284374499452/748851535403810856/mgg.png",

      player: [
        {
          name: "ironman",
          hp: 380,
          image1:
            "https://www.fightersgeneration.com/characters2/iron-man-stance.gif",
          image2:
            "https://www.fightersgeneration.com/characters2/iron-standattax.gif",
          image3:
            "https://www.fightersgeneration.com/characters2/iron-unibeam.gif"
        },
        {
          name: "captainamerica",
          hp: 360,
          image1:
            "https://www.fightersgeneration.com/characters/captainamerica-catch.gif",
          image2:
            "https://www.fightersgeneration.com/characters/captainamerica-upper.gif",
          image3:
            "https://www.fightersgeneration.com/characters/captainamerica-chargingstar.gif",
        },
        {
          name: "Hulk",
          hp: 390,
          image1:
            "https://www.fightersgeneration.com/characters/hulk-winpose21.gif",
          image2:
            "https://www.fightersgeneration.com/characters/hulk-special2.gif",
          image3:
            "https://www.fightersgeneration.com/characters/hulk-rox.gif",
        },
        
        
      ],
      monster: [
         {
          name: "Magneto",
          hp: 200,
          image1:
            "https://www.fightersgeneration.com/characters2/m-magneto.gif",
          image2:
            "https://www.fightersgeneration.com/characters2/magneto-hp.gif",
        },
        {
          name: "DR.DOOM",
          hp: 300,
          image1:
            "https://www.fightersgeneration.com/characters/m-doom.gif",
          image2:
            "https://www.fightersgeneration.com/characters/dr-shot.gif",
        },
      {
          name: "DR.DOOM",
          hp: 350,
          image1:
            "https://www.fightersgeneration.com/characters4/thanos-gif.gif",
          image2:
            "https://www.fightersgeneration.com/characters4/than-tele.gif",
        },
      ],
    };
  },

  props: {
    Label: String,
  },

  methods: {
    Start: function () {
      this.chosenNumber1 = Math.floor(Math.random() * this.player.length);
      this.randomPlayer = this.player[this.chosenNumber1].name;
      this.hp1 = this.player[this.chosenNumber1].hp;
      this.imagePlayer = this.player[this.chosenNumber1].image1;

      this.chosenNumber2 = Math.floor(Math.random() * this.monster.length);
      this.randomMonster = this.monster[this.chosenNumber2].name;
      this.hp2 = this.monster[this.chosenNumber2].hp;
      this.imageMonster = this.monster[this.chosenNumber2].image1;
      this.end = false;
    },

    randomenergy: function () {
      this.randomPlayerAttack = Math.max(Math.floor(Math.random() * 10) + 1, 3);
      this.hp2 -= this.randomPlayerAttack;
      this.imagePlayer = this.player[this.chosenNumber1].image2;      
      
      this.randomMonsterAttack = Math.max(Math.floor(Math.random() * 15) + 1,5);
      this.hp1 -= this.randomMonsterAttack;
      this.imageMonster = this.monster[this.chosenNumber2].image2;

      if (this.hp1 <= 0 & this.hp2 <=0) {
        this.hp1 = 0;
        this.hp2 = 0;
        this.end = true;             
      }
      else if (this.hp1 <= 0) {
        this.hp1 = 0;
        this.end = true;
        this.imageMonster = this.monster[this.chosenNumber2].image1;
      }
      else if (this.hp2 <= 0) {
        this.hp2 = 0;
        this.end = true;
        this.imagePlayer = this.player[this.chosenNumber1].image1;
      }
    },

    randomSpenergy: function () {
      this.randomPlayerAttack = Math.max(Math.floor(Math.random() * 20) + 1,10);
      this.hp2 -= this.randomPlayerAttack;
      this.imagePlayer = this.player[this.chosenNumber1].image3;      

      this.randomMonsterAttack = Math.max(Math.floor(Math.random() * 15) + 1,5);
      this.hp1 -= this.randomMonsterAttack;
      this.imageMonster = this.monster[this.chosenNumber2].image2;    

      if (this.hp1 <= 0 & this.hp2 <=0) {
        this.hp1 = 0;
        this.hp2 = 0;
        this.end = true;             
      }
      else if (this.hp1 <= 0) {
        this.hp1 = 0;
        this.end = true;
        this.imageMonster = this.monster[this.chosenNumber2].image1
      }
      else if (this.hp2 <= 0) {
        this.hp2 = 0;
        this.end = true;
        this.imagePlayer = this.player[this.chosenNumber1].image1;
      }
    },
  },
};
</script>

<style>
</style>