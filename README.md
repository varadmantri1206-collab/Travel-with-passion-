<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>AI Trip Planner</title>
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:'Poppins',sans-serif;
}
body{
    height:100vh;
    background: linear-gradient(135deg,#667eea,#764ba2);
    display:flex;
    justify-content:center;
    align-items:center;
}
.container{
    width:95%;
    max-width:900px;
    backdrop-filter: blur(20px);
    background: rgba(255,255,255,0.15);
    border-radius:20px;
    padding:30px;
    color:#fff;
    box-shadow:0 8px 32px rgba(0,0,0,0.3);
    animation:fadeIn 1s ease;
}
h1{
    text-align:center;
    margin-bottom:20px;
    font-weight:600;
}
form{
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:15px;
}
input, select, textarea{
    padding:10px;
    border-radius:10px;
    border:none;
    outline:none;
}
textarea{
    grid-column: span 2;
}
button{
    grid-column: span 2;
    padding:12px;
    border:none;
    border-radius:10px;
    background:#fff;
    color:#764ba2;
    font-weight:600;
    cursor:pointer;
    transition:0.3s;
}
button:hover{
    background:#f1f1f1;
    transform:scale(1.03);
}
.result{
    margin-top:20px;
    padding:15px;
    border-radius:10px;
    background:rgba(255,255,255,0.2);
    max-height:250px;
    overflow:auto;
}
.day{
    margin-bottom:10px;
}
@keyframes fadeIn{
    from{opacity:0; transform:translateY(20px);}
    to{opacity:1; transform:translateY(0);}
}
@media(max-width:600px){
    form{
        grid-template-columns:1fr;
    }
    textarea, button{
        grid-column: span 1;
    }
}
</style>
</head>
<body>

<div class="container">
    <h1>✨ Smart Trip Planner ✨</h1>
    <form id="tripForm">
        <input type="text" id="destination" placeholder="Destination" required>
        <input type="number" id="days" placeholder="Number of Days" required>
        <input type="number" id="budget" placeholder="Budget (₹)" required>
        <select id="interest" required>
            <option value="">Select Interest</option>
            <option>Adventure</option>
            <option>Relaxation</option>
            <option>Food</option>
            <option>Nature</option>
            <option>Historical</option>
        </select>
        <textarea id="notes" placeholder="Any special requests?"></textarea>
        <button type="submit">Generate Plan</button>
    </form>

    <div class="result" id="result"></div>
</div>

<script>
document.getElementById("tripForm").addEventListener("submit", function(e){
    e.preventDefault();

    const destination = document.getElementById("destination").value;
    const days = document.getElementById("days").value;
    const budget = document.getElementById("budget").value;
    const interest = document.getElementById("interest").value;
    const notes = document.getElementById("notes").value;

    let plan = `<h3>Your ${days}-Day Trip to ${destination}</h3>`;
    plan += `<p><strong>Budget:</strong> ₹${budget}</p><hr>`;

    for(let i=1;i<=days;i++){
        plan += `<div class="day">
                    <strong>Day ${i}:</strong> 
                    Explore ${destination}'s best ${interest.toLowerCase()} spots.
                    Enjoy local experiences and capture memories!
                 </div>`;
    }

    if(notes){
        plan += `<hr><p><strong>Special Notes:</strong> ${notes}</p>`;
    }

    document.getElementById("result").innerHTML = plan;
});
</script>

</body>
</html>
