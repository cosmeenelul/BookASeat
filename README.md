# 🪑 BookASeat – Aplicație Web si Mobile de Rezervare a locurilor la birou si a salilor de conferinta

Seat Booking este o aplicație modernă care ajută companiile să gestioneze rezervările de locuri și săli, să ofere informații despre disponibilitatea acestora și să ofere date utile despre trafic și vreme pentru utilizatori.  

Aplicația este structurată pe trei componente: **Backend**, **Frontend** și **Mobile**.

---

## ✨ Ce poate face aplicația

### 📌 Gestionarea rezervărilor
- Utilizatorii pot rezerva **locuri individuale** sau **săli întregi** pentru anumite intervale de timp.  
- Rezervările pot fi vizualizate după utilizator sau status și pot fi anulate dacă este necesar.

### 🏢 Gestionarea locurilor și sălilor
- Aplicația știe **care locuri sau săli sunt libere** și poate returna disponibilitatea pentru un anumit etaj sau cladire pe intervale de timp.  
- Permite organizarea spațiilor pe clădiri și etaje pentru o gestionare eficientă a rezervărilor.

### 🚗 Informații despre trafic și incidente
- Utilizatorii pot obține **timpul estimat pana la birou (ETA) si distanta**, ținând cont de trafic.  
- Aplicația afișează **incidentele de trafic** dintr-o anumită zonă, ajutând la planificarea traseului.

### 🌤️ Informații despre vreme
- Aplicația oferă **vremea curentă și prognoza pe următoarele 7 zile**, astfel încât utilizatorii să poată planifica rezervările în funcție de condițiile meteo.

---
## ⚙️ Partea tehnică️. Detaliile tehnice ale API-urilor pentru dezvoltatori.

## **Endpoint-uri API**

### **1. Reservations**
Gestionarea rezervărilor utilizatorilor.

| Endpoint                         | Method | Descriere |
|---------------------------------|--------|-----------|
| `/reservations/seats`            | POST   | Creează o rezervare pentru locuri. Body: `CreateReservationRequest` |
| `/reservations`                  | GET    | Returnează toate rezervările |
| `/reservations/user/{userId}`    | GET    | Returnează toate rezervările unui utilizator după `userId` |
| `/reservations/{reservationId}`  | PUT    | Anulează o rezervare după `reservationId` |
| `/reservations/rooms`            | POST   | Creează o rezervare pentru o cameră. Body: `CreateReservationRoomRequest` |
| `/reservations/user`             | GET    | Returnează rezervările unui utilizator filtrate după `status`. Parametri: `userId`, `status` |

---

### **2. Rooms**
Informații despre săli și rezervări.

| Endpoint                          | Method | Descriere |
|----------------------------------|--------|-----------|
| `/rooms/timeslots`                | GET    | Returnează time slot-urile ocupate pentru o cameră între `dateStart` și `dateEnd`. Parametri: `roomId`, `dateStart`, `dateEnd` |
| `/rooms/roomByFloorAndBuilding`   | GET    | Returnează toate sălile de pe un anumit etaj și clădire. Parametri: `floorName`, `buildingName` |

---

### **3. Seats**
Gestionarea locurilor de muncă.

| Endpoint                         | Method | Descriere |
|---------------------------------|--------|-----------|
| `/seats`                         | GET    | Returnează toate locurile |
| `/seats/freeSeats`               | GET    | Returnează locurile libere pe un anumit etaj și interval de timp. Parametri: `floorId`, `dateStart`, `dateEnd` |

---

### **4. Traffic**
Date despre trafic și incidente.

| Endpoint                         | Method | Descriere |
|---------------------------------|--------|-----------|
| `/traffic/directions`            | GET    | Returnează rute posibile între două puncte. Parametri: `start` (punct de pornire), `traffic` (dacă să includă traficul), `travelMode` (opțional) |
| `/traffic/incidents`             | GET    | Returnează toate incidentele de trafic dintr-o zonă definită. Parametru: `startBbox` (bounding box pentru zona de interes) |

---

### **5. Weather**
Date despre vreme curentă și prognoză.

| Endpoint         | Method | Descriere |
|-----------------|--------|-----------|
| `/api/weather`  | GET    | Returnează date despre vremea curentă și prognoza pentru următoarele 7 zile |

---


