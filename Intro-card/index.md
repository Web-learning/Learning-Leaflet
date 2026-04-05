/* Intro Card Overlay */
#intro-card {
  position: absolute;
  top: 70px;
  right: 20px;
  max-width: 320px;
  background: white;
  padding: 15px 20px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.2);
  border-radius: 6px;
  font-size: 1rem;
  z-index: 1000;
  line-height: 1.4;
  cursor: pointer;
  transition: opacity 0.3s ease;
}

/* Close button */
#intro-card .close-btn {
  position: absolute;
  top: 8px;
  right: 10px;
  font-size: 18px;
  cursor: pointer;
  color: #666;
}

#intro-card .close-btn:hover {
  color: #000;
}

<!-- Intro Card Overlay -->
  <div id="intro-card">
    <span class="close-btn">&times;</span>
    <p>
    This is where the intro card text goes.
    </p>
  </div>

// Close intro card
document.querySelector('#intro-card .close-btn')
  .addEventListener('click', function(e) {
    e.stopPropagation();
    document.getElementById('intro-card').style.display = 'none';
  });

// Clickable card action (optional)
document.getElementById('intro-card')
  .addEventListener('click', function() {
    alert('You can link this to a tour page or story map.');
  });
