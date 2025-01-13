---
layout: post
title: AP Statistics
permalink: classes/ap/stats/home
---
ma
<div class="class-home" style="font-family: 'Verdana', sans-serif; background: linear-gradient(to bottom, #E3F2FD, #90CAF9); min-height: 100vh; padding: 20px; box-sizing: border-box;">
  <h1 style="color: #42A5F5; text-align: center; font-size: 3em; animation: fadeIn 1s;">Welcome to AP Statistics</h1>

  <!-- Leaderboard Section -->
  <section id="leaderboard" style="background-color: #BBDEFB; padding: 20px; border-radius: 15px; margin: 20px auto; max-width: 600px; box-shadow: 0px 4px 15px rgba(0, 0, 0, 0.2); animation: slideIn 1.5s;">
    <h2 style="color: #1976D2; text-align: center;">Leaderboard</h2>
    <p style="text-align: center; color: #0D47A1; font-size: 1.1em;">Top scorers refreshed daily.</p>
    <ul id="leaderboard-list" style="list-style: none; padding: 0; text-align: center;">
      <!-- Leaderboard items will be dynamically injected -->
    </ul>
  </section>

  <!-- Take Quiz Button -->
  <section id="quiz-section" style="text-align: center; margin-top: 30px; animation: fadeIn 2s;">
    <h2 style="color: #1976D2; font-size: 2em;">Test Your Knowledge</h2>
    <p style="color: #0D47A1; font-size: 1.2em;">Click below to take the AP Statistics quiz!</p>
    <button id="take-quiz" onclick="navigateToQuiz()" 
            style="background: linear-gradient(45deg, #42A5F5, #64B5F6); border: none; color: white; padding: 15px 30px; font-size: 1.5em; border-radius: 50px; cursor: pointer; box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.3); transition: transform 0.2s, box-shadow 0.2s;">
      Take Quiz
    </button>
  </section>

  <!-- Flashcards Button -->
  <section id="flashcards-section" style="text-align: center; margin-top: 20px; animation: fadeIn 2.5s;">
    <h2 style="color: #1976D2; font-size: 2em;">Study with Flashcards</h2>
    <p style="color: #0D47A1; font-size: 1.2em;">Click below to explore and create flashcards for this class!</p>
    <button id="open-flashcards" onclick="navigateToFlashcards()" 
            style="background: linear-gradient(45deg, #42A5F5, #64B5F6); border: none; color: white; padding: 15px 30px; font-size: 1.5em; border-radius: 50px; cursor: pointer; box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.3); transition: transform 0.2s, box-shadow 0.2s;">
      Open Flashcards
    </button>
  </section>
</div>

<script>
  async function fetchLeaderboard() {
    try {
      const response = await fetch('/api/leaderboard/apstats');
      const leaderboard = await response.json();

      const leaderboardList = document.getElementById('leaderboard-list');
      leaderboardList.innerHTML = '';

      leaderboard.forEach((entry) => {
        const listItem = document.createElement('li');
        listItem.textContent = `${entry.username}: ${entry.score} points (${new Date(entry.date).toLocaleDateString()})`;
        listItem.style = "color: #1E88E5; margin: 10px 0; font-size: 1.2em; font-weight: bold;";
        leaderboardList.appendChild(listItem);
      });
    } catch (error) {
      console.error('Error fetching leaderboard:', error);
    }
  }

  function navigateToQuiz() {
    window.location.href = './quizz';
  }

  function navigateToFlashcards() {
    window.location.href = './flash';
  }

  fetchLeaderboard();
</script>

<style>
  /* Animations */
  @keyframes fadeIn {
    from {
      opacity: 0;
    }
    to {
      opacity: 1;
    }
  }

  @keyframes slideIn {
    from {
      transform: translateY(50px);
      opacity: 0;
    }
    to {
      transform: translateY(0);
      opacity: 1;
    }
  }

  /* Button Hover Effect */
  button:hover {
    transform: scale(1.05);
    box-shadow: 0px 6px 15px rgba(0, 0, 0, 0.4);
  }

  /* Leaderboard List Item Hover */
  #leaderboard-list li:hover {
    color: #64B5F6;
    transition: color 0.3s ease;
  }
</style>

<!-- Back to Index Button -->
<div style="text-align: center; margin-top: 30px;">
  <button onclick="goToIndex()" 
          style="background: #42A5F5; color: white; border: none; padding: 10px 20px; font-size: 1em; border-radius: 10px; cursor: pointer; box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.3); transition: transform 0.2s, box-shadow 0.2s;">
    Back to Index
  </button>
</div>

<script>
  function goToIndex() {
    window.location.href = '/cantella_frontend/';
  }
</script>