<template>
    <div id="map" style="height: 600px; width: 1200px"></div>
  </template>
  
  <script>
  import { onMounted } from 'vue';
  import L from 'leaflet';
  import 'leaflet/dist/leaflet.css';
  import 'leaflet-search/dist/leaflet-search.src.css';  // Importer les styles du plugin
  import 'leaflet-search';  // Importer le plugin
  
  export default {
    name: 'MapComponent',
    setup() {
      onMounted(() => {
        // Initialisation de la carte centrée sur le Cameroun
        const map = L.map('map').setView([3.8480, 11.5021], 7); // Centre du Cameroun
  
        // Ajouter les tuiles de la carte (OpenStreetMap)
        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
          maxZoom: 18,
          attribution: '© OpenStreetMap contributors'
        }).addTo(map);
  
        // Ajouter un marqueur au centre du Cameroun
        const marker = L.marker([3.8480, 11.5021]).addTo(map)
          .bindPopup('Cameroun')
          .openPopup();
  
        // Ajouter la barre de recherche
        const searchControl = new L.Control.Search({
          layer: L.layerGroup([marker]),  // Chercher uniquement dans le groupe de couches contenant le marqueur
          initial: false,
          zoom: 10,
          marker: false
        });
  
        map.addControl(searchControl);
      });
    }
  };
  </script>
  