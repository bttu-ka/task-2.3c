<template>
  <div class="football-match">
    
    <h2>Football Match Details</h2>
    <p>Home Team: {{ homeTeam }}</p> 
    <p>Away Team: {{ awayTeam }}</p>
    <p v-html="matchDescription"></p> 

    
    <p :id="venueId"></p> 

    
    <p>Match Date: {{ matchDate }}</p> 

    
    <button @click="startMatch">Start Match</button> 

    
    <h2>Match Score</h2>
    <p>Total Goals: {{ totalGoals }}</p>
    

    
    <h2>Player on the field </h2>
    <ul>
      <li v-for="player in players" :key="player.id">{{ player.name }}</li> 
    </ul>

    
    <button @click="scoreGoal">Score a Goal</button> 
    

    
    <h2>Enter Match Details</h2>
    <label for="goals">Goals:</label>
    <input type="number" v-model="goals" /> 
    <br />
    
    <label for="manOfTheMatch">Man of the Match:</label>
    <select v-model="manOfTheMatch">
      <option value="player1">Messi</option>
      <option value="player2">Ronaldo</option>
    </select> 
    <br />
    <label for="matchSummary">Match Summary:</label>
    <textarea v-model="matchSummary"></textarea>

    
    <h2>Football Match Components</h2>
    <match-summary :summary="matchSummary"></match-summary> 
    <player-stats @goal="handleGoalEvent"></player-stats> 
    <slot-example>
     
    </slot-example>
  </div>
</template>

<script setup>
import { ref, computed, watch } from 'vue';

//Match Details
const homeTeam = ref('Home Team');
const awayTeam = ref('Away Team');
const matchDescription = '<p>An exciting football match!</p>';
const venueId = 'football-stadium';
const matchDate = '2023-09-15';

//Match Methods
const startMatch = () => {
  alert('Match has started!');
};

//Match Score
const totalGoals = ref(0);

//Player List
const players = ref([
  { id: 1, name: 'Messi' },
  { id: 2, name: 'Ronaldo' },
  { id: 3, name: 'Mbappe' },
]);

// Event Handling
const scoreGoal = () => {
  totalGoals.value++;
};



//Football Match Form
const goals = ref(0);
const manOfTheMatch = ref('');
const matchSummary = ref('');




const handleGoalEvent = (data) => {

};
</script>

<style>
.football-match {
  font-family: Arial, sans-serif;
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  background-color: pink;
  border: 1px solid #bb1f1f;
  box-shadow: 0 0 10px rgba(244, 236, 6, 0.1);
}

h2 {
  color: red;
  margin-top: 10px;
}

p {
  margin: 5px 0;
}

button {
  background-color: #007bff;
  color: #e2bd29;
  border: none;
  padding: 10px 20px;
  margin-top: 10px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  margin: 5px 0;
}

label {
  display: block;
  margin-top: 10px;
  font-weight: bold;
}

input[type="number"],
select,
textarea {
  width: 100%;
  padding: 5px;
  margin: 5px 0;
  border: 1px solid #e3ff13;
  border-radius: 3px;
}
</style>
