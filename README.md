<section id="nearby-clinics" style="padding: 60px 20px; background: #f4f7f9;">
  <h2 style="text-align:center; margin-bottom: 40px; font-size: 32px; color: #333;">Nearby Dental Clinics</h2>

  <!-- Search & Filter -->
  <div style="max-width: 800px; margin: auto; display:flex; flex-wrap: wrap; gap: 15px; justify-content: center; margin-bottom: 50px;">
    <input type="text" id="searchInput" placeholder="Search by clinic name..." style="padding:10px; flex:1 1 250px; border-radius:6px; border:1px solid #ccc;">
    
    <select id="serviceFilter" style="padding:10px; border-radius:6px; border:1px solid #ccc;">
      <option value="">Filter by service</option>
      <option value="General Dentistry">General Dentistry</option>
      <option value="Teeth Whitening">Teeth Whitening</option>
      <option value="Orthodontics">Orthodontics</option>
      <option value="Implants">Implants</option>
      <option value="Urgent Care">Urgent Care</option>
    </select>

    <select id="ratingFilter" style="padding:10px; border-radius:6px; border:1px solid #ccc;">
      <option value="">Filter by rating</option>
      <option value="5">5 stars</option>
      <option value="4">4+ stars</option>
      <option value="3">3+ stars</option>
    </select>
  </div>

  <div class="clinic-container">

    <!-- Clinic 1 -->
    <div class="clinic-card" data-name="Chinatown Service Center Dental Clinic" data-services="General Dentistry,Teeth Whitening,Orthodontics,Implants" data-rating="4">
      <h3>Chinatown Service Center Dental Clinic</h3>
      <p><span class="icon">📍</span> 2110 S. Hacienda Blvd., Hacienda Heights, CA 91745</p>
      <p><span class="icon">⏰</span> Tue–Sat: 8:30 AM – 5:00 PM</p>
      <p><span class="icon">📞</span> (213) 808-1700 | cscinfo@cscla.org</p>

      <p><strong>Rating:</strong> <span class="stars"></span></p>

      <button class="toggle-btn">View Services</button>
      <div class="collapsible">
        Comprehensive oral exams, X-rays, fillings, extractions, crowns, bridges, veneers, dentures, root canals (front teeth), Invisalign, nightguards, teeth whitening, implants.
      </div>

      <a href="https://www.google.com/maps/search/?api=1&query=2110+S.+Hacienda+Blvd.,+Hacienda+Heights,+CA+91745" target="_blank" class="map-btn">
        Open in Google Maps
      </a>
    </div>

    <!-- Clinic 2 -->
    <div class="clinic-card" data-name="St. John's Community Health – S. Mark Taper Foundation Health Center" data-services="General Dentistry,Urgent Care" data-rating="4.7">
      <h3>St. John's Community Health – S. Mark Taper Foundation Health Center</h3>
      <p><span class="icon">📍</span> 808 W 58th St, Los Angeles, CA 90037</p>
      <p><span class="icon">⏰</span> Mon–Fri: 8:00 AM – 5:00 PM, Sat: 7:00 AM – 3:30 PM</p>
      <p><span class="icon">📞</span> (323) 541-1411</p>

      <p><strong>Rating:</strong> <span class="stars"></span></p>

      <button class="toggle-btn">View Services</button>
      <div class="collapsible">
        Comprehensive dental care, routine exams, cleanings, fillings, urgent dental services.
      </div>

      <a href="https://www.google.com/maps/search/?api=1&query=808+W+58th+St,+Los+Angeles,+CA+90037" target="_blank" class="map-btn">
        Open in Google Maps
      </a>
    </div>

  </div>

  <style>
    .clinic-container {
      display: flex;
      flex-wrap: wrap;
      gap: 30px;
      justify-content: center;
    }

    .clinic-card {
      flex: 1 1 320px;
      background: #fff;
      padding: 25px 20px;
      border-radius: 12px;
      box-shadow: 0 6px 15px rgba(0,0,0,0.1);
      transition: transform 0.3s, box-shadow 0.3s;
      display: flex;
      flex-direction: column;
      gap: 12px;
    }

    .clinic-card:hover {
      transform: translateY(-8px);
      box-shadow: 0 12px 25px rgba(0,0,0,0.15);
    }

    .clinic-card h3 {
      color: #2c3e50;
      margin-bottom: 12px;
    }

    .icon {
      margin-right: 6px;
    }

    .map-btn {
      display:inline-block;
      padding:12px 18px;
      background:#4285F4;
      color:white;
      border-radius:6px;
      text-decoration:none;
      text-align: center;
      margin-top: 10px;
      font-weight: 500;
      transition: background 0.3s;
    }

    .map-btn:hover { background:#3367d6; }

    .toggle-btn {
      background:#4CAF50;
      color:white;
      padding:10px;
      border:none;
      border-radius:5px;
      cursor:pointer;
      transition: background 0.3s;
      font-weight: 500;
    }

    .toggle-btn:hover { background:#45a049; }

    .collapsible {
      overflow: hidden;
      max-height: 0;
      transition: max-height 0.5s ease, padding 0.3s ease;
      margin-top: 10px;
      line-height: 1.6;
      color: #555;
    }

    .stars { display:inline-block; color: #FFD700; font-size: 18px; }

    @media (max-width: 768px) {
      .clinic-container { flex-direction: column; gap: 25px; }
    }
  </style>

  <script>
    // Collapsible functionality
    document.querySelectorAll('.toggle-btn').forEach(button => {
      button.addEventListener('click', () => {
        const content = button.nextElementSibling;
        if(content.style.maxHeight && content.style.maxHeight !== '0px'){
          content.style.maxHeight = null;
          content.style.paddingTop = '0px';
          content.style.paddingBottom = '0px';
        } else {
          content.style.maxHeight = content.scrollHeight + "px";
          content.style.paddingTop = '10px';
          content.style.paddingBottom = '10px';
        }
      });
    });

    // Dynamic Star Rating
    function renderStars(){
      document.querySelectorAll('.stars').forEach(starEl => {
        let rating = parseFloat(starEl.parentElement.parentElement.getAttribute('data-rating'));
        let fullStars = Math.floor(rating);
        let halfStar = (rating - fullStars >= 0.5) ? 1 : 0;
        let emptyStars = 5 - fullStars - halfStar;
        let starsHtml = '★'.repeat(fullStars);
        if(halfStar) starsHtml += '⯨'; // half star symbol
        starsHtml += '☆'.repeat(emptyStars);
        starEl.innerHTML = starsHtml;
      });
    }

    renderStars();

    // Search & Filter functionality
    const searchInput = document.getElementById('searchInput');
    const serviceFilter = document.getElementById('serviceFilter');
    const ratingFilter = document.getElementById('ratingFilter');
    const cards = document.querySelectorAll('.clinic-card');

    function filterCards() {
      const search = searchInput.value.toLowerCase();
      const service = serviceFilter.value;
      const rating = parseFloat(ratingFilter.value);
      cards.forEach(card => {
        const name = card.getAttribute('data-name').toLowerCase();
        const services = card.getAttribute('data-services');
        const cardRating = parseFloat(card.getAttribute('data-rating'));
        let matches = true;

        if(search && !name.includes(search)) matches = false;
        if(service && !services.includes(service)) matches = false;
        if(ratingFilter.value && cardRating < rating) matches = false;

        card.style.display = matches ? 'flex' : 'none';
      });
    }

    searchInput.addEventListener('input', filterCards);
    serviceFilter.addEventListener('change', filterCards);
    ratingFilter.addEventListener('change', filterCards);
  </script>
</section>
