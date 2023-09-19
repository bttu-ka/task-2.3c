<template>
  <div class="football-match">
    //Football Match Details
    <h2>Football Match Details</h2>
    <p>Home Team: {{ homeTeam }}</p>
    <p>Away Team: {{ awayTeam }}</p>
    <p v-html="matchDescription"></p>

    <!-- 2. Match Venue -->
    <p :id="venueId"></p>

    <!-- 3. Match Date -->
    <p>Match Date: {{ matchDate }}</p>

    <!-- 4. Football Match Methods -->
    <button @click="startMatch">Start Match</button>

    <!-- 5. Match Score -->
    <h2>Match Score</h2>
    <p>Total Goals: {{ totalGoals }}</p>

    <!-- 6. Players on the Field -->
    <h2>Players on the Field</h2>
    <ul>
      <li v-for="player in players" :key="player.id">{{ player.name }}</li>
    </ul>

    <!-- 7. Event Handling: Football Match Events -->
    <button @click="scoreGoal">Score a Goal</button>

    <!-- 8. Football Match Form -->
    <h2>Enter Match Details</h2>
    <label for="goals">Goals:</label>
    <input type="number" v-model.number="goals" /> <!-- Added v-model.number -->
    <br />
    <label for="manOfTheMatch">Man of the Match:</label>
    <select v-model="manOfTheMatch">
      <option value="player1">Messi</option>
      <option value="player2">Ronaldo</option>
    </select>
    <br />
    <label for="matchSummary">Match Summary:</label>
    <textarea v-model.trim="matchSummary"></textarea> <!-- Added v-model.trim -->

    <!-- 9. Football Match Watchers -->
    <p>Goals Watcher: {{ goalsWatcher }}</p>

    <!-- 10. Football Match Components -->
    <h2>Football Match Components</h2>
    <slot-example>
      <!-- c. Slots -->
      <div slot="football-slot">Football Slot Content</div>
    </slot-example>
  </div>
</template>

<script setup>
import { ref, computed, watch } from 'vue';

// Match Details
const homeTeam = ref('Home Team');
const awayTeam = ref('Away Team');
const matchDescription = '<p>An exciting football match!</p>';
const venueId = 'football-stadium';
const matchDate = '2023-09-15';

// 4. Football Match Methods
const startMatch = () => {
  alert('Match has started!');
};

// 5. Match Score
const totalGoals = ref(0);

// 6. Player List
const players = ref([
  { id: 1, name: 'Messi' },
  { id: 2, name: 'Ronaldo' },
  { id: 3, name: 'Mbappe' },
]);

// 7. Event Handling: Football Match Events 
const scoreGoal = () => {
  totalGoals.value++;
};

// Football Match Form
const goals = ref(0);
const manOfTheMatch = ref('');
const matchSummary = ref('');

// 9. Football Match Watchers
const goalsWatcher = computed(() => {
  return goals.value > 5 ? 'High scoring match!' : 'Normal match.';
});

// 10. Football Match Components (Not shown here)
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
