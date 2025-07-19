leak-door/
│
├── index.html         ← Home/Track page
├── css/
│   └── styles.css     ← Basic styling
└── js/
    └── track.js       ← Tracking logic (simulated)
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Leak Door Courier Service</title>
  <link rel="stylesheet" href="css/styles.css">
</head>
<body>
  <header>
    <h1>Leak Door Courier Service</h1>
    <nav>
      <a href="#">Home</a> |
      <a href="#">Track</a> |
      <a href="#">Contact</a>
    </nav>
  </header>

  <main>
    <section id="tracking-section">
      <h2>Track Your Shipment</h2>
      <form id="track-form">
        <input type="text" id="awb" placeholder="Enter AWB Number" required>
        <button type="submit">Track</button>
      </form>
      <div id="tracking-result"></div>
    </section>
  </main>

  <footer>
    <p>© 2025 Leak Door Courier Service. All rights reserved.</p>
  </footer>

  <script src="js/track.js"></script>
</body>
</html>
* {
  box-sizing: border-box;
  margin: 0; padding: 0;
}
body {
  font-family: Arial, sans-serif;
  line-height: 1.6;
  padding: 20px;
  background: #f9f9f9;
}
header {
  background: #0074D9;
  color: #fff;
  padding: 20px;
  text-align: center;
}
nav a {
  color: #fff;
  text-decoration: none;
  margin: 0 10px;
}
main {
  margin: 20px auto;
  max-width: 600px;
  background: #fff;
  padding: 20px;
  border-radius: 5px;
}
#tracking-result {
  margin-top: 20px;
  padding: 15px;
  border: 1px solid #ddd;
  border-radius: 4px;
  min-height: 100px;
}
footer {
  text-align: center;
  margin-top: 40px;
  color: #666;
}
document.getElementById('track-form').addEventListener('submit', function(e) {
  e.preventDefault();
  const awb = document.getElementById('awb').value.trim();
  const resultDiv = document.getElementById('tracking-result');
  resultDiv.innerHTML = '🔍 Looking up...';

  // Simulate server delay
  setTimeout(() => {
    const fakeDB = {
      'LD123456789': {
        status: 'In Transit',
        location: 'Austin, TX',
        eta: 'July 25, 2025'
      },
      'LD987654321': {
        status: 'Delivered',
        location: 'Houston, TX',
        deliveredOn: 'July 18, 2025'
      }
    };

    const info = fakeDB[awb];
    if (info) {
      resultDiv.innerHTML = `
        <strong>Status:</strong> ${info.status}<br>
        <strong>Location:</strong> ${info.location}<br>
        ${info.eta ? `<strong>ETA:</strong> ${info.eta}<br>` : ''}
        ${info.deliveredOn ? `<strong>Delivered On:</strong> ${info.deliveredOn}` : ''}
      `;
    } else {
      resultDiv.innerHTML = '⚠️ AWB number not found. Please check and try again.';
    }
  }, 700); // 0.7s delay
});
