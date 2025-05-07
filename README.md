<read.me>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Animal Alert Network</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background-color: #ffffff;
      color: #000000;
    }
    header {
      background-color: #f8f9fa;
      color: #333;
      padding: 15px;
      text-align: center;
    }
    nav {
      background-color: #e9ecef;
      display: flex;
      justify-content: center;
      gap: 20px;
      padding: 10px;
    }
    nav a {
      color: #007bff;
      text-decoration: none;
      font-weight: bold;
    }
    nav a:hover {
      color: #0056b3;
    }
    .map-container {
      display: flex;
      height: 500px;
    }
    .map-sidebar {
      width: 300px;
      background: #f1f1f1;
      padding: 20px;
      overflow-y: auto;
      box-shadow: 2px 0 5px rgba(0,0,0,0.1);
    }
    .map-sidebar h3 {
      margin-top: 0;
      color: #000;
    }
    .map-sidebar input[type="text"], .map-sidebar select {
      width: 100%;
      padding: 8px;
      margin-bottom: 15px;
      border: 1px solid #ccc;
      border-radius: 4px;
      background-color: #fff;
      color: #000;
    }
    .map-sidebar button {
      width: 100%;
      padding: 10px;
      background-color: #007bff;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
    .map-sidebar button:hover {
      background-color: #0056b3;
    }
    .map {
      flex-grow: 1;
    }
    #map {
      width: 100%;
      height: 100%;
    }
    .flyer-section {
      margin-top: 20px;
      padding: 20px;
      background-color: #f9f9f9;
      text-align: center;
    }
    .flyer-section h2, .flyer-section p {
      color: #000;
    }
    .flyer-section a {
      display: inline-block;
      margin: 10px;
      padding: 12px 24px;
      background-color: #007bff;
      color: white;
      text-decoration: none;
      border-radius: 5px;
    }
    .flyer-section a:hover {
      background-color: #0056b3;
    }
  </style>
<style>
  .toast {
    position: fixed;
    bottom: 20px;
    right: 20px;
    background-color: #28a745;
    color: white;
    padding: 12px 20px;
    border-radius: 5px;
    font-size: 14px;
    box-shadow: 0 0 10px rgba(0,0,0,0.2);
    z-index: 1000;
    animation: fadeOut 4s forwards;
  }
  @keyframes fadeOut {
    0% { opacity: 1; }
    80% { opacity: 1; }
    100% { opacity: 0; display: none; }
  }
</style>
</head>
<body>
  
  <a id="notifyButton" href="#" style="display: inline-block; margin-top: 20px; background-color: #ffcc00; color: #000; padding: 12px 20px; font-weight: bold; border-radius: 5px; text-decoration: none; font-size: 16px;">Notify Your Local Animal Services</a>
<script>
  fetch('https://ipapi.co/json/')
    .then(response => response.json())
    .then(data => {
      const city = data.city;
      const region = data.region;
      if (city && region) {
        const link = `https://www.google.com/search?q=animal+control+${encodeURIComponent(city + ' ' + region)}`;
        document.getElementById("notifyButton").href = link;
      } else {
        document.getElementById("notifyButton").href = "#";
        document.getElementById("notifyButton").textContent = "Search Animal Services Near You";
      }
    })
    .catch(() => {
      document.getElementById("notifyButton").href = "https://www.google.com/search?q=animal+control+near+me";
      document.getElementById("notifyButton").textContent = "Search Animal Services Near You";
    });
    });
</script>
<a href="#" id="signupButton" style="display: inline-block; margin-top: 20px; background-color: #007bff; color: white; padding: 12px 20px; font-weight: bold; border-radius: 5px; text-decoration: none; font-size: 16px;">Sign Up</a>
</header>
  <nav>
    <a href="#lost">Lost Pet Flyer</a>
    <a href="#found">Found Pet Flyer</a>
  </nav>

  <div class="map-container">
    <div class="map-sidebar">
      <h3>Report Location</h3>
      <input type="text" id="location" placeholder="Enter address or location...">
      <button onclick="geocodeAddress()">Locate on Map</button>
      <h3>Select Animal</h3>
      <div style="display: flex; align-items: center; gap: 10px;">
        <select id="animalType" onchange="updateAnimalPreview()">
          <option value="dog">Dog</option>
          <option value="cat">Cat</option>
          <option value="skunk">Skunk</option>
          <option value="horse">Horse</option>
          <option value="cow">Cow</option>
          <option value="possum">Possum</option>
          <option value="deer">Deer</option>
          <option value="raccoon">Raccoon</option>
          <option value="fox">Fox</option>
          <option value="coyote">Coyote</option>
          <option value="rabbit">Rabbit</option>
          <option value="bird">Bird</option>
        </select>
        <img id="animalPreview" src="https://img.icons8.com/emoji/48/dog.png" alt="Animal Icon" width="32" height="32" />
      </div>
      <p style="color: #444; font-size: 14px;">Click on the street location on the map and select the type of animal seen in the road.</p>

      <div class="flyer-section">
        <h2 style="font-size: 16px;">Create Lost Animal Flyer</h2>
        <p style="font-size: 13px;">Use our Canva template to design and share your Lost Pet flyer:</p>
        <a href="https://www.canva.com/design/DAGmt-u7ynY/k5GiXwZQqJvzFwGgLSgJ5Q/edit?ui=eyJBIjp7fX0" target="_blank" style="font-size: 13px; padding: 8px 16px;">Create Lost Flyer on Canva</a>

        <h2 style="margin-top:25px; font-size: 16px;">Create Found Animal Flyer</h2>
        <p style="font-size: 13px;">Use our Canva template to design and share your Found Pet flyer:</p>
        <a href="https://www.canva.com/design/DAGmt-u7ynY/k5GiXwZQqJvzFwGgLSgJ5Q/edit?ui=eyJBIjp7fX0" target="_blank" style="font-size: 13px; padding: 8px 16px;">Create Found Flyer on Canva</a>
      </div>
    </div>
    <div class="map">
      <div id="map"></div>
    </div>
  </div>
  <div style="padding: 20px; background-color: #f1f1f1;">
    <h3>Placed Animal Marker Log</h3>
    <ul id="markerLog" style="padding-left: 20px; font-size: 14px;"></ul>
  </div>

  <script>
  let map;
  let geocoder;
  const allMarkers = [];
  const icons = {
  dog: 'https://img.icons8.com/emoji/48/dog.png',
  cat: 'https://img.icons8.com/emoji/48/cat.png',
  skunk: 'https://img.icons8.com/color/48/skunk.png',
  horse: 'https://img.icons8.com/emoji/48/horse-face.png',
  cow: 'https://img.icons8.com/emoji/48/cow.png',
  possum: 'https://img.icons8.com/color/48/rodent.png',
  deer: 'https://img.icons8.com/color/48/deer.png',
  raccoon: 'https://img.icons8.com/color/48/raccoon.png',
  fox: 'https://img.icons8.com/color/48/fox.png',
  coyote: 'https://img.icons8.com/color/48/wolf.png',
  rabbit: 'https://img.icons8.com/emoji/48/rabbit.png',
  bird: 'https://img.icons8.com/emoji/48/bird-emoji.png'
};

  function initMap() {
    map = new google.maps.Map(document.getElementById("map"), {
      center: { lat: 37.7749, lng: -122.4194 },
      zoom: 12
    });
    geocoder = new google.maps.Geocoder();

    map.addListener("click", (e) => {
      const selected = document.getElementById("animalType").value;
      const iconExists = icons[selected] !== undefined;
      const marker = new google.maps.Marker({
        position: e.latLng,
        map,
        icon: iconExists ? icons[selected] : null,
        draggable: true
      });
      allMarkers.push(marker);

      marker.addListener("rightclick", () => {
        marker.setMap(null);
      });

      geocoder.geocode({ location: e.latLng }, (results, status) => {
        if (status === 'OK' && results[0]) {
          const address = results[0].formatted_address;
          document.getElementById("location").value = address;
          const toast = document.createElement("div");
          toast.className = "toast";
          toast.textContent = `✔️ Animal icon placed at: ${address}`;
          document.body.appendChild(toast);
          setTimeout(() => toast.remove(), 4000);
          if (!icons[selected]) {
            const labelMarker = new google.maps.Marker({
              position: e.latLng,
              map,
              label: selected.charAt(0).toUpperCase() + selected.slice(1),
              icon: {
                path: google.maps.SymbolPath.CIRCLE,
                scale: 0 // hides the icon so only label shows
              }
            });
            allMarkers.push(labelMarker);
          }
          const log = document.getElementById("markerLog");
          const entry = document.createElement("li");
          const img = document.createElement("img");
          img.src = icons[selected];
          img.alt = selected;
          img.style.width = "24px";
          img.style.height = "24px";
          img.style.verticalAlign = "middle";
          img.style.marginRight = "8px";
          entry.appendChild(img);
          entry.appendChild(document.createTextNode(`${selected.charAt(0).toUpperCase() + selected.slice(1)} icon placed at: ${address}`));
          log.appendChild(entry);
          console.log(`Marker logged: ${selected} at ${address}`);
        }
      });
    });

    const resetButton = document.createElement("button");
    resetButton.textContent = "Reset Map";
    resetButton.style.marginTop = "20px";
    resetButton.style.width = "100%";
    resetButton.style.backgroundColor = "#dc3545";
    resetButton.style.color = "white";
    resetButton.style.border = "none";
    resetButton.style.borderRadius = "5px";
    resetButton.style.padding = "10px";
    resetButton.style.cursor = "pointer";
    resetButton.addEventListener("click", () => {
      allMarkers.forEach(marker => marker.setMap(null));
      allMarkers.length = 0;
      document.getElementById("markerLog").innerHTML = "";
      document.getElementById("location").value = "";
    });
    document.querySelector(".map-sidebar").appendChild(resetButton);
  }
</script>
<script async src="https://maps.googleapis.com/maps/api/js?key=AIzaSyAzmt3_LNj7AiOJg7kBIRjDRsIsXrnESa4&callback=initMap">// Analytics for user location
fetch('https://ipapi.co/json/')
  .then(response => response.json())
  .then(data => {
    console.log(`User is located in: ${data.city}, ${data.region}`);
  });

</script>
</body>
</html>

