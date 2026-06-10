---
layout: homepage
---

<!-- ⭐blogs（书影音评+摄影超链接）摄影、山地民宿、红莲小学、万里学院等设计项目 notion页面 -->
<!-- 以后我的地图可以增加lived visited的所有点+图例-->

<div class="travel-map-shell">
  <div class="travel-map-layout">
    <div id="world-map-container" class="travel-map-canvas">
      <p id="loading-text">Map loading...</p>
      <div class="map-controls" aria-label="Map controls">
        <div class="basemap-toggle" aria-label="Basemap style">
          <button type="button" data-basemap="map">Map</button>
          <button type="button" data-basemap="satellite">Satellite</button>
        </div>
        <div class="map-zoom-controls" aria-label="Zoom controls">
          <button type="button" data-map-control="zoom-in" aria-label="Zoom in" title="Zoom in">+</button>
          <button type="button" data-map-control="zoom-out" aria-label="Zoom out" title="Zoom out">-</button>
          <button type="button" data-map-control="reset" aria-label="Reset map view" title="Reset map view">↻</button>
        </div>
      </div>
      <div id="map-place-card" class="map-place-card" aria-live="polite"></div>
    </div>
    <aside class="travel-timeline" aria-label="Place timeline">
      <div class="travel-timeline-title">Places</div>
      <div id="travel-timeline-list"></div>
    </aside>
  </div>
  <p class="travel-map-note">Click a marker or timeline item to explore each place.</p>
</div>

<style>
    .travel-map-shell {
      font-family: inherit;
      margin: 0 0 28px;
    }

    .travel-map-note {
      color: #666;
      font-size: 13px;
    }

    .travel-map-layout {
      display: grid;
      grid-template-columns: minmax(0, 1fr) 220px;
      gap: 12px;
      min-height: 500px;
    }

    .travel-map-canvas {
      background: #f7f7f4;
      border: 1px solid #e5e5e5;
      border-radius: 8px;
      min-height: 500px;
      overflow: hidden;
      position: relative;
    }

    #loading-text {
      color: #999;
      left: 50%;
      margin: 0;
      position: absolute;
      text-align: center;
      top: 50%;
      transform: translate(-50%, -50%);
    }

    .map-controls {
      align-items: flex-end;
      display: flex;
      flex-direction: column;
      gap: 5px;
      position: absolute;
      right: 10px;
      top: 10px;
      z-index: 1000;
    }

    .leaflet-container {
      background: #e6e1d7;
      color: #222;
      font-family: inherit;
      min-height: 500px;
      width: 100%;
    }

    .leaflet-control-attribution {
      font-size: 10px;
    }

    .leaflet-div-icon,
    .travel-map-marker-icon {
      background: transparent;
      border: 0;
      height: 0 !important;
      margin: 0 !important;
      width: 0 !important;
    }

    .map-marker {
      display: block;
      height: 0;
      position: relative;
      transform: none;
      width: 0;
      white-space: nowrap;
    }

    .map-marker-dot {
      background: #f4a5c8;
      border: 2px solid #fff;
      border-radius: 999px;
      box-shadow: 0 2px 10px rgba(216, 27, 114, 0.24);
      box-sizing: border-box;
      height: 14px;
      left: 0;
      position: absolute;
      top: 0;
      transform: translate(-50%, -50%);
      width: 14px;
      z-index: 1;
    }

    .map-marker-dot::after {
      animation: map-breathe 2.2s ease-in-out infinite;
      background: #f4a5c8;
      border-radius: inherit;
      content: "";
      inset: -2px;
      opacity: 0.55;
      position: absolute;
      z-index: -1;
    }

    .map-marker-loved .map-marker-dot {
      background: #f5d56e;
      box-shadow: 0 2px 8px rgba(120, 88, 18, 0.22);
    }

    .map-marker-loved .map-marker-dot::after {
      animation: none;
      background: #f5d56e;
      opacity: 0.22;
      transform: scale(1.9);
    }

    .map-marker.active .map-marker-dot,
    .map-marker:hover .map-marker-dot {
      background: var(--site-pink);
      box-shadow: 0 0 0 4px rgba(255, 255, 255, 0.72), 0 3px 14px rgba(0, 0, 0, 0.42);
    }

    .map-marker.active .map-marker-dot::after,
    .map-marker:hover .map-marker-dot::after {
      background: var(--site-pink);
    }

    @keyframes map-breathe {
      0% { transform: scale(1); opacity: 0.68; }
      50% { transform: scale(3.4); opacity: 0.14; }
      100% { transform: scale(1); opacity: 0.68; }
    }

    .fallback-basemap-active.leaflet-container,
    .fallback-basemap-active .leaflet-container {
      background: #f7f7f4;
    }

    .map-place-card a {
      background: rgba(255, 255, 255, 0.96);
      border: 1px solid #dcdcdc;
      border-radius: 6px;
      color: var(--site-blue);
      cursor: pointer;
      font-family: inherit;
      font-size: 12px;
      font-weight: 700;
      padding: 5px 8px;
    }

    .map-zoom-controls {
      background: rgba(255, 255, 255, 0.82);
      border: 1px solid #dcdcdc;
      border-radius: 999px;
      display: flex;
      gap: 2px;
      padding: 2px;
    }

    .map-zoom-controls button {
      align-items: center;
      background: transparent;
      border: 0;
      border-radius: 50%;
      color: var(--site-muted);
      cursor: pointer;
      display: inline-flex;
      font-family: inherit;
      font-size: 13px;
      font-weight: 700;
      height: 25px;
      justify-content: center;
      line-height: 1;
      padding: 0;
      transition: background-color 0.18s ease, box-shadow 0.18s ease, color 0.18s ease;
      width: 25px;
    }

    .map-zoom-controls button:hover {
      background: #fff;
      box-shadow: 0 1px 6px rgba(23, 49, 95, 0.14);
      color: var(--site-blue);
    }

    .basemap-toggle {
      background: rgba(255, 255, 255, 0.82);
      border: 1px solid #dcdcdc;
      border-radius: 999px;
      display: grid;
      gap: 2px;
      grid-template-columns: 1fr 1fr;
      padding: 2px;
    }

    .basemap-toggle button {
      background: transparent;
      border: 0;
      border-radius: 999px;
      color: var(--site-muted);
      min-width: 58px;
      padding: 5px 8px;
      transition: background-color 0.18s ease, box-shadow 0.18s ease, color 0.18s ease;
    }

    .basemap-toggle button.active {
      background: #fff;
      box-shadow: 0 1px 6px rgba(23, 49, 95, 0.18);
      color: var(--site-blue);
    }

    .map-place-card {
      background: rgba(255, 255, 255, 0.97);
      border: 1px solid #e1e1e1;
      border-radius: 8px;
      bottom: 14px;
      box-shadow: 0 6px 18px rgba(0, 0, 0, 0.12);
      left: 14px;
      max-width: 280px;
      padding: 12px;
      position: absolute;
      z-index: 1000;
    }

    .map-place-card h3 {
      color: var(--site-blue);
      font-size: 16px;
      margin: 0 0 6px;
    }

    .map-place-card p {
      color: #333;
      font-size: 12px;
      line-height: 1.5;
      margin: 0 0 10px;
    }

    .travel-timeline {
      border: 1px solid #e5e5e5;
      border-radius: 8px;
      max-height: 500px;
      overflow: auto;
      padding: 12px;
    }

    .travel-timeline-title {
      color: var(--site-blue);
      font-size: 14px;
      font-weight: 800;
      margin-bottom: 10px;
    }

    .timeline-group + .timeline-group {
      margin-top: 16px;
    }

    .timeline-group-title {
      align-items: center;
      color: var(--site-muted);
      display: flex;
      font-size: 12px;
      font-weight: 700;
      gap: 6px;
      letter-spacing: 0;
      margin: 0 0 8px;
      text-transform: uppercase;
    }

    .timeline-group-empty {
      border: 1px dashed #e4e7ec;
      border-radius: 8px;
      color: #7a8492;
      font-size: 12px;
      line-height: 1.35;
      padding: 9px 10px;
    }

    .timeline-item {
      background: #fff;
      border: 1px solid #e7e7e7;
      border-radius: 8px;
      cursor: pointer;
      font-family: inherit;
      margin-bottom: 10px;
      padding: 10px;
      transition: border-color 0.2s ease, box-shadow 0.2s ease;
    }

    .timeline-item:hover,
    .timeline-item.active {
      border-color: var(--site-pink);
      box-shadow: 0 4px 12px var(--site-pink-soft);
    }

    .timeline-item-date {
      color: #777;
      font-size: 11px;
      margin-bottom: 4px;
    }

    .timeline-item-name {
      color: var(--site-blue);
      font-size: 14px;
      font-weight: 800;
    }

    .timeline-item-role {
      color: #555;
      font-size: 11px;
      line-height: 1.35;
      margin-top: 4px;
    }

    @media print, screen and (max-width: 700px) {
      .travel-map-layout {
        grid-template-columns: 1fr;
      }

      .travel-map-canvas,
      .leaflet-container {
        min-height: 390px;
      }

      .travel-timeline {
        max-height: none;
      }
    }

</style>

<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css">
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

<script>
(function() {
    const defaultPhotoUrl = "https://500px.com/p/ruaruaxu";

    const container = document.querySelector("#world-map-container");
    const loadingText = document.querySelector("#loading-text");
    const card = document.querySelector("#map-place-card");
    const timeline = document.querySelector("#travel-timeline-list");

    const placeGroups = [
      {
        id: "lived",
        title: "Lived",
        places: [
          { name: "Hefei", date: "Birth-2019", role: "Hometown", coords: [31.8206, 117.2272], desc: "Home sweet home.", photoUrl: defaultPhotoUrl },
          { name: "Shanghai", date: "2019 - 2023", role: "B.Eng. @ Tongji", coords: [31.2304, 121.4737], desc: "Architecture and Urban Design at Tongji University.", photoUrl: defaultPhotoUrl },
          { name: "Beijing", date: "2023 - 2025", role: "M.Arch. @ Tsinghua", coords: [39.9042, 116.4074], desc: "Urban Informatics and Urban Renewal at Tsinghua University.", photoUrl: defaultPhotoUrl },
          { name: "Berkeley", date: "2025 - Present", role: "PhD @ UC Berkeley", coords: [37.8719, -122.2585], desc: "Environmental Planning at UC Berkeley.", photoUrl: defaultPhotoUrl }
        ]
      },
      {
        id: "loved",
        title: "Loved",
        places: [
          {
            name: "Lhatse",
            date: "2021",
            role: "Lhatse County, Shigatse, Tibet",
            timelineRole: "Dream Classroom Volunteer",
            coords: [29.0932, 87.6374],
            desc: "Dream Classroom project at Lhatse County Complete Primary School.",
            photoUrl: "https://mp.weixin.qq.com/s/Ey6OsoMCLCJfH4P7ziNsDg",
            linkLabel: "Read story"
          },
          {
            name: "Huocheng",
            date: "2022",
            role: "Huocheng County, Ili, Xinjiang",
            timelineRole: "Dream Classroom Volunteer",
            coords: [44.0625, 80.8765],
            desc: "Dream Classroom project at Huocheng County Middle School.",
            photoUrl: "https://mp.weixin.qq.com/s/i5wdBYEOpGJl6prYkR5HWg",
            linkLabel: "Read story"
          },
          {
            name: "Hong Kong",
            date: "2023",
            role: "Undergraduate thesis",
            coords: [22.3193, 114.1694],
            desc: "Port-Oriented and Landscape Urbanism: Hong Kong-Shenzhen Border Urban Design.",
            photoUrl: defaultPhotoUrl
          },
          {
            name: "Milan",
            date: "2024",
            role: "Lombardy, Italy",
            coords: [45.4642, 9.1900],
            desc: "Cultural exchange in Italy as an Interdisciplinary Design Innovation Scholar Program.",
            photoUrl: defaultPhotoUrl,
            journey: {
              id: "italy-2024",
              name: "Italy",
              date: "2024",
              role: "Interdisciplinary Design Innovation Scholar Program"
            }
          },
          {
            name: "Florence",
            date: "2024",
            role: "Tuscany, Italy",
            coords: [43.7696, 11.2558],
            desc: "Cultural exchange in Italy as an Interdisciplinary Design Innovation Scholar Program.",
            photoUrl: defaultPhotoUrl,
            journey: {
              id: "italy-2024",
              name: "Italy",
              date: "2024",
              role: "Interdisciplinary Design Innovation Scholar Program"
            }
          },
          {
            name: "Siena",
            date: "2024",
            role: "Tuscany, Italy",
            coords: [43.3188, 11.3308],
            desc: "Cultural exchange in Italy as an Interdisciplinary Design Innovation Scholar Program.",
            photoUrl: defaultPhotoUrl,
            journey: {
              id: "italy-2024",
              name: "Italy",
              date: "2024",
              role: "Interdisciplinary Design Innovation Scholar Program"
            }
          },
          {
            name: "Venice",
            date: "2024",
            role: "Veneto, Italy",
            coords: [45.4408, 12.3155],
            desc: "Cultural exchange in Italy as an Interdisciplinary Design Innovation Scholar Program.",
            photoUrl: defaultPhotoUrl,
            journey: {
              id: "italy-2024",
              name: "Italy",
              date: "2024",
              role: "Interdisciplinary Design Innovation Scholar Program"
            }
          },
          {
            name: "Tokyo",
            date: "2025",
            role: "Tokyo, Japan",
            coords: [35.6762, 139.6503],
            desc: "Graduation trip in Japan.",
            photoUrl: defaultPhotoUrl,
            journey: {
              id: "japan-2025",
              name: "Japan",
              date: "2025",
              role: "Graduation trip"
            }
          },
          {
            name: "Yokohama",
            date: "2025",
            role: "Kanagawa, Japan",
            coords: [35.4437, 139.6380],
            desc: "Graduation trip in Japan.",
            photoUrl: defaultPhotoUrl,
            journey: {
              id: "japan-2025",
              name: "Japan",
              date: "2025",
              role: "Graduation trip"
            }
          },
          {
            name: "Kamakura",
            date: "2025",
            role: "Kanagawa, Japan",
            coords: [35.3192, 139.5467],
            desc: "Graduation trip in Japan.",
            photoUrl: defaultPhotoUrl,
            journey: {
              id: "japan-2025",
              name: "Japan",
              date: "2025",
              role: "Graduation trip"
            }
          },
          {
            name: "Taiyuan",
            date: "2023",
            role: "Shanxi, China",
            coords: [37.8706, 112.5489],
            desc: "Jundi Travel Scholarship trip in Shanxi.",
            photoUrl: defaultPhotoUrl,
            journey: {
              id: "shanxi-2023",
              name: "Shanxi",
              date: "2023",
              role: "Jundi Travel Scholarship"
            }
          },
          {
            name: "Datong",
            date: "2023",
            role: "Shanxi, China",
            coords: [40.0768, 113.3001],
            desc: "Jundi Travel Scholarship trip in Shanxi.",
            photoUrl: defaultPhotoUrl,
            journey: {
              id: "shanxi-2023",
              name: "Shanxi",
              date: "2023",
              role: "Jundi Travel Scholarship"
            }
          },
          {
            name: "Mount Wutai",
            date: "2023",
            role: "Shanxi, China",
            coords: [39.0063, 113.5931],
            desc: "Jundi Travel Scholarship trip in Shanxi.",
            photoUrl: defaultPhotoUrl,
            journey: {
              id: "shanxi-2023",
              name: "Shanxi",
              date: "2023",
              role: "Jundi Travel Scholarship"
            }
          }
        ]
      }
    ];

    const myLocations = placeGroups.flatMap(group => (
      group.places.map(place => ({ ...place, group: group.id }))
    ));

    const tracks = [
        { from: "Hefei", to: "Shanghai" },
        { from: "Shanghai", to: "Beijing" },
        { from: "Beijing", to: "Berkeley" }
    ];

    if (!container || !window.L) {
      if (loadingText) {
        loadingText.textContent = "Map failed to load.";
        loadingText.style.color = "red";
      }
      return;
    }

    function renderCard(d) {
      card.innerHTML = `
        <h3>${d.name}</h3>
        <p><strong>${d.date}</strong><br>${d.role}<br>${d.desc}</p>
        <a href="${d.photoUrl}" target="_blank" rel="noopener">${d.linkLabel || "View photos"}</a>
      `;
    }

    function renderJourneyCard(entry) {
      const placeNames = entry.places.map(place => place.name).join(", ");
      card.innerHTML = `
        <h3>${entry.name}</h3>
        <p><strong>${entry.date}</strong><br>${placeNames}<br>${entry.role}</p>
        <a href="${defaultPhotoUrl}" target="_blank" rel="noopener">View photos</a>
      `;
    }

    loadingText.remove();

    const initialView = { center: [20, 0], zoom: 1 };
    const satelliteTileUrl = "https://server.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer/tile/{z}/{y}/{x}";
    const satelliteLabelUrl = "https://services.arcgisonline.com/ArcGIS/rest/services/Reference/World_Boundaries_and_Places/MapServer/tile/{z}/{y}/{x}";
    const mapTileUrl = "https://{s}.basemaps.cartocdn.com/light_all/{z}/{x}/{y}{r}.png";
    const map = L.map(container, {
      attributionControl: true,
      maxBounds: [[-85, -180], [85, 180]],
      maxBoundsViscosity: 0.8,
      minZoom: 1,
      scrollWheelZoom: true,
      worldCopyJump: false,
      zoomControl: false
    }).setView(initialView.center, initialView.zoom);

    const satelliteBase = L.tileLayer(satelliteTileUrl, {
      attribution: "Tiles &copy; Esri",
      maxZoom: 18
    });

    const satelliteLabels = L.tileLayer(satelliteLabelUrl, {
      attribution: "Labels &copy; Esri",
      maxZoom: 18
    });

    const fallbackBasemap = L.tileLayer(mapTileUrl, {
      attribution: "&copy; OpenStreetMap contributors &copy; CARTO",
      maxZoom: 18
    });
    let currentBasemap = "";
    let satelliteHasFailed = false;
    const basemapButtons = Array.from(document.querySelectorAll("[data-basemap]"));

    function updateBasemapButton() {
      basemapButtons.forEach(button => {
        const isActive = button.dataset.basemap === currentBasemap;
        button.classList.toggle("active", isActive);
        button.setAttribute("aria-pressed", String(isActive));
      });
    }

    function setBasemap(type, forcedByError = false) {
      if (type === currentBasemap) return;
      [satelliteBase, satelliteLabels, fallbackBasemap].forEach(layer => {
        if (map.hasLayer(layer)) {
          map.removeLayer(layer);
        }
      });

      if (type === "satellite" && !satelliteHasFailed) {
        satelliteBase.addTo(map);
        satelliteLabels.addTo(map);
        container.classList.remove("fallback-basemap-active");
        currentBasemap = "satellite";
      } else {
        fallbackBasemap.addTo(map);
        container.classList.add("fallback-basemap-active");
        currentBasemap = "map";
      }

      if (forcedByError) {
        basemapButtons.forEach(button => {
          button.title = "Satellite tiles failed to load, so the map switched to the local basemap.";
        });
      }
      updateBasemapButton();
    }

    function handleSatelliteError() {
      satelliteHasFailed = true;
      setBasemap("map", true);
    }

    satelliteBase.on("tileerror", handleSatelliteError);
    satelliteLabels.on("tileerror", handleSatelliteError);

    setBasemap("map");

    const locationMap = {};
    myLocations.forEach(d => { locationMap[d.name] = d; });

    function curvedTrackSegments(start, end) {
      const pointCount = 96;
      const startLat = start.coords[0];
      const startLng = start.coords[1];
      const endLat = end.coords[0];
      let endLng = end.coords[1];
      let lngDelta = endLng - startLng;

      if (Math.abs(lngDelta) > 180) {
        endLng += lngDelta > 0 ? -360 : 360;
        lngDelta = endLng - startLng;
      }

      const distance = Math.hypot(endLat - startLat, lngDelta);
      const lift = Math.min(Math.max(distance * 0.16, 4), 22);
      const controlLat = Math.min(Math.max((startLat + endLat) / 2 + lift, -70), 78);
      const controlLng = (startLng + endLng) / 2;
      const unwrappedCoords = [];

      for (let i = 0; i <= pointCount; i += 1) {
        const t = i / pointCount;
        const lat = ((1 - t) ** 2 * startLat) + (2 * (1 - t) * t * controlLat) + (t ** 2 * endLat);
        const lng = ((1 - t) ** 2 * startLng) + (2 * (1 - t) * t * controlLng) + (t ** 2 * endLng);
        unwrappedCoords.push([lat, lng]);
      }

      const segments = [[]];
      unwrappedCoords.forEach((coord, index) => {
        const [lat, lng] = coord;
        const previous = unwrappedCoords[index - 1];

        if (previous && ((previous[1] <= 180 && lng > 180) || (previous[1] >= -180 && lng < -180))) {
          const boundary = lng > 180 ? 180 : -180;
          const previousLat = previous[0];
          const previousLng = previous[1];
          const ratio = (boundary - previousLng) / (lng - previousLng);
          const boundaryLat = previousLat + ratio * (lat - previousLat);
          const currentSegment = segments[segments.length - 1];

          currentSegment.push([boundaryLat, boundary]);
          segments.push([[boundaryLat, boundary === 180 ? -180 : 180]]);
        }

        const normalizedLng = lng > 180 ? lng - 360 : (lng < -180 ? lng + 360 : lng);
        segments[segments.length - 1].push([lat, normalizedLng]);
      });

      return segments.filter(segment => segment.length > 1);
    }

    function drawTrack(trackCoords) {
      L.polyline(trackCoords, {
        color: "#ffffff",
        lineCap: "round",
        lineJoin: "round",
        opacity: 0.78,
        smoothFactor: 0,
        weight: 4
      }).addTo(map);
      L.polyline(trackCoords, {
        color: getComputedStyle(document.documentElement).getPropertyValue("--site-pink").trim() || "#d81b72",
        lineCap: "round",
        lineJoin: "round",
        opacity: 0.96,
        smoothFactor: 0,
        weight: 2
      }).addTo(map);
    }

    tracks.forEach(track => {
      const start = locationMap[track.from];
      const end = locationMap[track.to];
      if (!start || !end) return;
      curvedTrackSegments(start, end).forEach(drawTrack);
    });

    const markerItems = new Map();
    const timelineItems = new Map();

    function timelineSortValue(date) {
      const text = String(date || "");
      if (/present/i.test(text)) return 9999;
      const years = text.match(/\d{4}/g);
      return years ? parseInt(years[years.length - 1], 10) : -Infinity;
    }

    function getTimelineEntries(group) {
      const entries = [];
      const journeyEntries = new Map();

      group.places.forEach(d => {
        if (!d.journey) {
          entries.push({
            key: `place:${d.name}`,
            type: "place",
            date: d.date,
            name: d.name,
            role: d.timelineRole || d.role,
            place: d
          });
          return;
        }

        if (!journeyEntries.has(d.journey.id)) {
          const entry = {
            key: `journey:${d.journey.id}`,
            type: "journey",
            id: d.journey.id,
            date: d.journey.date,
            name: d.journey.name,
            role: d.journey.role,
            places: []
          };
          journeyEntries.set(d.journey.id, entry);
          entries.push(entry);
        }
        journeyEntries.get(d.journey.id).places.push(d);
      });

      if (group.id === "loved" || group.id === "lived") {
        entries.sort((a, b) => timelineSortValue(b.date) - timelineSortValue(a.date));
      }

      return entries;
    }

    function markerHtml(d) {
      return `
        <div class="map-marker map-marker-${d.group}" data-location="${d.name}">
          <span class="map-marker-dot"></span>
        </div>
      `;
    }

    placeGroups.forEach(group => {
      const groupEl = document.createElement("div");
      groupEl.className = "timeline-group";
      groupEl.dataset.group = group.id;

      const groupTitle = document.createElement("div");
      groupTitle.className = "timeline-group-title";
      groupTitle.textContent = group.title;
      groupEl.appendChild(groupTitle);

      if (!group.places.length) {
        const empty = document.createElement("div");
        empty.className = "timeline-group-empty";
        empty.textContent = "Travel places to add later.";
        groupEl.appendChild(empty);
      }

      getTimelineEntries(group).forEach(entry => {
        const item = document.createElement("button");
        item.className = "timeline-item";
        item.type = "button";
        item.innerHTML = `
          <div class="timeline-item-date">${entry.date}</div>
          <div class="timeline-item-name">${entry.name}</div>
          <div class="timeline-item-role">${entry.role}</div>
        `;
        item.addEventListener("click", () => {
          if (entry.type === "journey") {
            setActiveJourney(entry);
          } else {
            setActiveLocation(entry.place);
          }
        });
        groupEl.appendChild(item);
        timelineItems.set(entry.key, item);
      });

      timeline.appendChild(groupEl);
    });

    myLocations.forEach(d => {
      const marker = L.marker(d.coords, {
        icon: L.divIcon({
          className: "travel-map-marker-icon",
          html: markerHtml(d),
          iconSize: [1, 1],
          iconAnchor: [0, 0]
        }),
        zIndexOffset: d.group === "lived" ? 1000 : 0
      }).addTo(map);

      marker.on("click", () => setActiveLocation(d));
      markerItems.set(d.name, marker);
    });

    function setActiveLocation(d, shouldZoom = true) {
      const activeTimelineKey = d.journey ? `journey:${d.journey.id}` : `place:${d.name}`;
      renderCard(d);
      markerItems.forEach((marker, name) => {
        const markerEl = marker.getElement();
        if (markerEl) {
          markerEl.querySelector(".map-marker")?.classList.toggle("active", name === d.name);
        }
      });
      timelineItems.forEach((item, key) => {
        item.classList.toggle("active", key === activeTimelineKey);
      });
      if (shouldZoom) {
        map.flyTo(d.coords, 5, { duration: 0.8 });
      }
    }

    function setActiveJourney(entry) {
      renderJourneyCard(entry);
      markerItems.forEach((marker, name) => {
        const markerEl = marker.getElement();
        const isInJourney = entry.places.some(place => place.name === name);
        if (markerEl) {
          markerEl.querySelector(".map-marker")?.classList.toggle("active", isInJourney);
        }
      });
      timelineItems.forEach((item, key) => {
        item.classList.toggle("active", key === entry.key);
      });
      map.fitBounds(entry.places.map(place => place.coords), {
        maxZoom: 5,
        padding: [32, 32]
      });
    }

    document.querySelector('[data-map-control="zoom-in"]').addEventListener("click", () => {
      map.zoomIn();
    });
    document.querySelector('[data-map-control="zoom-out"]').addEventListener("click", () => {
      map.zoomOut();
    });
    document.querySelector('[data-map-control="reset"]').addEventListener("click", () => {
      map.flyTo(initialView.center, initialView.zoom, { duration: 0.6 });
    });
    basemapButtons.forEach(button => {
      button.addEventListener("click", () => {
        if (button.dataset.basemap === "satellite") {
          satelliteHasFailed = false;
          basemapButtons.forEach(item => item.removeAttribute("title"));
        }
        setBasemap(button.dataset.basemap);
      });
    });

    setActiveLocation(myLocations.find(location => location.name === "Berkeley") || myLocations[0], false);
})();
</script>

👋🦁Hi! I am a first-year Ph.D. student in Environmental Planning at UC Berkeley, where I am fortunate to be advised by [Prof. Lu Liang](https://sites.google.com/site/liang3mlab/people/prof-lu-liang) ([LAEP](https://ced.berkeley.edu/land)) and work closely with [Prof. Emma Pierson](https://people.eecs.berkeley.edu/~emmapierson/) ([EECS](https://eecs.berkeley.edu/), [BAIR](https://bair.berkeley.edu/)).

My research lies at the intersection of **AI for Science** and **trustworthy AI**, with a broader commitment to **AI for Social Good**. I focus on model evaluation, alignment, interpretability, and fairness in complex real-world settings. More specifically, I develop spatial data science and machine learning methods to study **how multiple hazards, urban environments, and social systems interact to shape exposure, vulnerability, and everyday life**, with the goal of building AI systems that support scientific understanding, decision-making, and socially beneficial applications, including more equitable planning and policy. My recent work includes:

- **Environmental Hazards & Health:** measuring human exposure to and health impacts of heat, air pollution, wildfire, flooding, and compound hazards.

- **Urban Environments & Social Equity:** spatial perception disparity ([Cities, 2025](https://wenruixu.com/assets/files/publication/j.cities.2025.106278.pdf)), mobility & air pollution ([SCS, 2025](https://wenruixu.com/assets/files/publication/xuSpatiotemporalImpactsPurposespecific2025.pdf)), urban renewal, and healthcare networks.

- **LLM & Geospatial Foundation Model:** LLM alignment for spatial and aesthetical understanding ([ACL, 2025](https://aclanthology.org/2025.acl-long.567/)), geospatial applications and interpretability.

Previously, I received my M.Arch. from [Tsinghua University](https://www.tsinghua.edu.cn/en/) in 2025 and B.Eng. from [Tongji University](https://caup.tongji.edu.cn/caupen/main.htm) with the highest distinction in 2023. I also worked as a researcher intern at Tsinghua [FIB-Lab](https://fi.ee.tsinghua.edu.cn/) ([Department of Electronic Engineering](https://www.ee.tsinghua.edu.cn/en/)), planning and architectural intern at [THUDPI](http://www.thupdi.com/) and [THAD](https://www.thad.com.cn/), contributing to two built projects, and equity research intern at [Kaiyuan Securities Research Institute](https://www.kysec.cn/index.php?m=content&c=index&a=lists&catid=107).

I am so lucky to have learned from and worked with many wonderful people! **[[🏅My collaborators & mentors]](./people)**.
<br>


## News

{% include_relative _includes/news.md %}

## Selected Work

Full-text PDFs of all publications are available for download **[[here]](./publications)**.<br>
†Equal Contribution, *Corresponding Author

{% include_relative _includes/selected_publications.md %}

## Misc

- I love the 90s Alternative Rock, Britpop, Citypop, and Classicals (especially in the Impressionism Era), and recently I have been especially into dreampop and shoegaze. My favorite contemporary artists include: Blur, Big Thief, Radiohead, 万能青年旅店, Neutral Milk Hotel, The Velvet Underground, Pink Floyd, My Bloody Valentine, My Little Airport, Cheer Chen, Coldplay... So hard to name them all! Here are my collections on [RateYourMusic](https://rateyourmusic.com/~ruaruaxu) or [Douban](https://www.douban.com/people/xycf/)!
- I watch about 200+ movies each year. **Movies let us live three times more lives.** We can talk on [Letterboxd](https://letterboxd.com/ruaruaxu/) or [Douban](https://www.douban.com/people/xycf/)! My favorite directors are Quentin Tarantino, Woody Allen, David Fincher, Sofia Coppola... My life movie is "The Lord of The Rings", "Yi Yi" by Edward Yang, and "The Secret Life of Walter Mitty". My favorite TV by now is "ロングバケーション"(Long Vacation).
- Unfortunately I don't have time to read as many books each year, but I'd love to get any recommendations on [Goodreads](https://goodreads.com/ruaruaxu) or [Douban](https://www.douban.com/people/xycf/)!
- I enjoy "city walking" and photography. You can find my photos in my blogs and on [500px](https://500px.com/p/ruaruaxu).
- I am so addicted to tennis. I was a member of the Tsinghua School of Architecture Tennis Team. I've been learning piano since 22 (I can play Chopin's Waltz in A Minor now! Hope I can play Debussy's La Fille aux Cheveux de Lin and Liszt's Liebesträume one day!). I also play guitar and have long hoped to start a band, though it still hasn't happened yet.🎾🎹🎸
- I am a "No spicy, no joy" person, and my "spiritual hometown" is Sichuan.😈
- My nickname is ruarua or rua.😁

<div id='contact'></div>

## Contact

I am always excited to meet fellow researchers with shared interests!<br>
Please feel free to contact me via Email or WeChat.

- **Email:** <span style="color:var(--site-pink);">wenruixu(at)outlook(dot)com</span>
- **WeChat:** <span style="color:var(--site-pink);">ruaruaxu</span>

## Guestbook

{% include_relative _includes/giscus.html %}


<script type='text/javascript' id='clustrmaps' src='//cdn.clustrmaps.com/map_v2.js?cl=d3d3d3&w=a&t=tt&d=rb3p-HLpB7vIKlMArS_N1cPimHsZnd9RNzFFiMPkdw8&co=ffffff&ct=002676&cmo=002676&cmn=ff1796'></script>
