<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Leadership Impact Poll</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');
        body { font-family: 'Inter', sans-serif; }
        .vote-animation {
            animation: voteSubmit 0.6s ease-out;
        }
        @keyframes voteSubmit {
            0% { transform: scale(1); }
            50% { transform: scale(1.02); }
            100% { transform: scale(1); }
        }
        .result-bar {
            transition: width 0.8s ease-out;
        }
        .option-hover:hover {
            transform: translateY(-1px);
            transition: transform 0.2s ease;
        }
    </style>
</head>
<body class="bg-gradient-to-br from-blue-50 to-indigo-100 min-h-screen py-8 px-4">
    <div class="max-w-4xl mx-auto">
        <!-- Header -->
        <div class="text-center mb-8">
            <h1 class="text-3xl font-bold text-gray-800 mb-4">Leadership Impact Poll</h1>
            <p class="text-lg text-gray-600 max-w-3xl mx-auto leading-relaxed">
                When you think about the most successful leaders you've worked with, which outcomes best describe their impact on the team?
            </p>
        </div>

        <!-- Poll Container -->
        <div class="bg-white rounded-2xl shadow-xl p-8 mb-6">
            <!-- Voting Section -->
            <div id="votingSection">
                <h3 class="text-xl font-semibold text-gray-800 mb-6">Select all that apply:</h3>
                
                <div class="space-y-4 mb-8">
                    <label class="option-hover flex items-start p-4 border-2 border-gray-200 rounded-xl cursor-pointer hover:border-blue-300 hover:bg-blue-50 transition-all duration-200">
                        <input type="checkbox" value="belonging" class="mt-1 mr-4 w-5 h-5 text-blue-600 rounded focus:ring-blue-500">
                        <span class="text-gray-700 font-medium">A strong sense of belonging among team members</span>
                    </label>
                    
                    <label class="option-hover flex items-start p-4 border-2 border-gray-200 rounded-xl cursor-pointer hover:border-blue-300 hover:bg-blue-50 transition-all duration-200">
                        <input type="checkbox" value="engagement" class="mt-1 mr-4 w-5 h-5 text-blue-600 rounded focus:ring-blue-500">
                        <span class="text-gray-700 font-medium">High levels of engagement and motivation</span>
                    </label>
                    
                    <label class="option-hover flex items-start p-4 border-2 border-gray-200 rounded-xl cursor-pointer hover:border-blue-300 hover:bg-blue-50 transition-all duration-200">
                        <input type="checkbox" value="innovation" class="mt-1 mr-4 w-5 h-5 text-blue-600 rounded focus:ring-blue-500">
                        <span class="text-gray-700 font-medium">Greater innovation and creative problem-solving</span>
                    </label>
                    
                    <label class="option-hover flex items-start p-4 border-2 border-gray-200 rounded-xl cursor-pointer hover:border-blue-300 hover:bg-blue-50 transition-all duration-200">
                        <input type="checkbox" value="performance" class="mt-1 mr-4 w-5 h-5 text-blue-600 rounded focus:ring-blue-500">
                        <span class="text-gray-700 font-medium">Increased team effectiveness and performance</span>
                    </label>
                    
                    <label class="option-hover flex items-start p-4 border-2 border-gray-200 rounded-xl cursor-pointer hover:border-blue-300 hover:bg-blue-50 transition-all duration-200">
                        <input type="checkbox" value="other" class="mt-1 mr-4 w-5 h-5 text-blue-600 rounded focus:ring-blue-500">
                        <span class="text-gray-700 font-medium">Other (please share in the chat)</span>
                    </label>
                </div>
                
                <button id="submitVote" class="w-full bg-blue-600 hover:bg-blue-700 text-white font-semibold py-4 px-8 rounded-xl transition-colors duration-200 disabled:opacity-50 disabled:cursor-not-allowed">
                    Submit Your Vote
                </button>
            </div>

            <!-- Results Section -->
            <div id="resultsSection" class="mt-8 pt-8 border-t border-gray-200">
                <div class="flex justify-between items-center mb-6">
                    <h3 class="text-xl font-semibold text-gray-800">Live Results</h3>
                    <span id="totalVotes" class="text-sm text-gray-600 bg-gray-100 px-3 py-1 rounded-full">0 votes</span>
                </div>
                
                <div class="space-y-6">
                    <div class="result-item">
                        <div class="flex justify-between items-center mb-2">
                            <span class="text-gray-700 font-medium">A strong sense of belonging among team members</span>
                            <span id="belonging-percent" class="text-blue-600 font-semibold">0%</span>
                        </div>
                        <div class="w-full bg-gray-200 rounded-full h-3">
                            <div id="belonging-bar" class="result-bar bg-blue-500 h-3 rounded-full" style="width: 0%"></div>
                        </div>
                        <div id="belonging-count" class="text-sm text-gray-500 mt-1">0 votes</div>
                    </div>
                    
                    <div class="result-item">
                        <div class="flex justify-between items-center mb-2">
                            <span class="text-gray-700 font-medium">High levels of engagement and motivation</span>
                            <span id="engagement-percent" class="text-green-600 font-semibold">0%</span>
                        </div>
                        <div class="w-full bg-gray-200 rounded-full h-3">
                            <div id="engagement-bar" class="result-bar bg-green-500 h-3 rounded-full" style="width: 0%"></div>
                        </div>
                        <div id="engagement-count" class="text-sm text-gray-500 mt-1">0 votes</div>
                    </div>
                    
                    <div class="result-item">
                        <div class="flex justify-between items-center mb-2">
                            <span class="text-gray-700 font-medium">Greater innovation and creative problem-solving</span>
                            <span id="innovation-percent" class="text-purple-600 font-semibold">0%</span>
                        </div>
                        <div class="w-full bg-gray-200 rounded-full h-3">
                            <div id="innovation-bar" class="result-bar bg-purple-500 h-3 rounded-full" style="width: 0%"></div>
                        </div>
                        <div id="innovation-count" class="text-sm text-gray-500 mt-1">0 votes</div>
                    </div>
                    
                    <div class="result-item">
                        <div class="flex justify-between items-center mb-2">
                            <span class="text-gray-700 font-medium">Increased team effectiveness and performance</span>
                            <span id="performance-percent" class="text-orange-600 font-semibold">0%</span>
                        </div>
                        <div class="w-full bg-gray-200 rounded-full h-3">
                            <div id="performance-bar" class="result-bar bg-orange-500 h-3 rounded-full" style="width: 0%"></div>
                        </div>
                        <div id="performance-count" class="text-sm text-gray-500 mt-1">0 votes</div>
                    </div>
                    
                    <div class="result-item">
                        <div class="flex justify-between items-center mb-2">
                            <span class="text-gray-700 font-medium">Other (please share in the chat)</span>
                            <span id="other-percent" class="text-gray-600 font-semibold">0%</span>
                        </div>
                        <div class="w-full bg-gray-200 rounded-full h-3">
                            <div id="other-bar" class="result-bar bg-gray-500 h-3 rounded-full" style="width: 0%"></div>
                        </div>
                        <div id="other-count" class="text-sm text-gray-500 mt-1">0 votes</div>
                    </div>
                </div>
                

            </div>
        </div>

        <!-- Instructions -->
        <div class="text-center text-gray-600">
            <p class="text-sm">Results update in real-time as participants submit their votes</p>
        </div>
    </div>

    <script>
        // Poll data storage
        let pollData = {
            belonging: 0,
            engagement: 0,
            innovation: 0,
            performance: 0,
            other: 0,
            totalVotes: 0
        };

        // Load existing data from localStorage
        const savedData = localStorage.getItem('leadershipPollData');
        if (savedData) {
            pollData = JSON.parse(savedData);
            updateResults();
        }

        const submitButton = document.getElementById('submitVote');
        const votingSection = document.getElementById('votingSection');
        const resultsSection = document.getElementById('resultsSection');


        // Handle vote submission
        submitButton.addEventListener('click', function() {
            const checkboxes = document.querySelectorAll('input[type="checkbox"]:checked');
            
            if (checkboxes.length === 0) {
                alert('Please select at least one option before submitting your vote.');
                return;
            }

            // Add animation
            votingSection.classList.add('vote-animation');

            // Record votes
            checkboxes.forEach(checkbox => {
                pollData[checkbox.value]++;
            });
            pollData.totalVotes++;

            // Save to localStorage
            localStorage.setItem('leadershipPollData', JSON.stringify(pollData));

            // Update results after animation
            setTimeout(() => {
                updateResults();
            }, 600);
        });



        // Update results display
        function updateResults() {
            const total = pollData.totalVotes;
            
            // Update total votes
            document.getElementById('totalVotes').textContent = `${total} vote${total !== 1 ? 's' : ''}`;

            // Update each option
            Object.keys(pollData).forEach(key => {
                if (key !== 'totalVotes') {
                    const count = pollData[key];
                    const percentage = total > 0 ? Math.round((count / total) * 100) : 0;
                    
                    const percentElement = document.getElementById(`${key}-percent`);
                    const barElement = document.getElementById(`${key}-bar`);
                    const countElement = document.getElementById(`${key}-count`);
                    
                    if (percentElement && barElement && countElement) {
                        percentElement.textContent = `${percentage}%`;
                        barElement.style.width = `${percentage}%`;
                        countElement.textContent = `${count} vote${count !== 1 ? 's' : ''}`;
                    }
                }
            });
        }

        // Enable submit button when at least one option is selected
        document.querySelectorAll('input[type="checkbox"]').forEach(checkbox => {
            checkbox.addEventListener('change', function() {
                const anyChecked = document.querySelectorAll('input[type="checkbox"]:checked').length > 0;
                submitButton.disabled = !anyChecked;
            });
        });

        // Initially disable submit button
        submitButton.disabled = true;
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'980aaac265221460',t:'MTc1ODEzMzc0NS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
