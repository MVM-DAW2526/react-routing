# 🚀 Plataforma de Gestió per a una "Escape Room" Interactiva

## 📝 Descripció del projecte

Treballes per a una empresa d'oci que necessita una aplicació web interna per monitoritzar les partides de les seves sales d'Escape Room. L'aplicació permetrà als "Game Masters" (operadors) controlar el temps dels equips, enviar pistes en temps real, gestionar reserves i veure estadístiques sense que l'aplicació perdi l'estat del temporitzador general.

------------------------------

## 🧩 Requisits tècnics i estructura de rutes

Hauràs de dissenyar l'arquitectura de l'aplicació implementant les següents rutes i lògiques utilitzant React Router:

### 1. Accés i Seguretat (/login)

* Pàgina de Login: Una pantalla simple on l'operador introdueix les seves credencials.
* Ruta Protegida (Auth Guard): Tota la resta de l'aplicació ha d'estar protegida. Si un usuari intenta entrar directament a qualsevol altra URL sense haver iniciat sessió, l'aplicació l'ha de redirigir automàticament a /login recordant la intenció original.

### 2. El Panell de Control Principal (/dashboard)

* Layout Compartit: Aquesta ruta actua com a base arquitectònica. Ha de tenir una barra lateral fixa amb el nom de l'operador, notificacions globals d'alerta i el menú de navegació.
* Contenidor dinàmic (<Outlet />): La part central de la pantalla carregarà les sub-rutes.

### 3. Sub-rutes del Dashboard (Rutes Anidades)

* Pantalla d'Inici (/dashboard): Mostra un resum amb el nombre de sales actives avui i un botó de "Començar Nova Partida".
* Llista de Sales (/dashboard/rooms):
* Mostra targetes (cards) de les diferents sales temàtiques disponibles (ex: "Laboratori Zombi", "Missió Espacial", "El Castell").
   * Filtres per URL (Query Params): Implementa un cercador i uns botons de filtratge per dificultat (Fàcil/Mitjà/Difícil). En canviar el filtre, la URL ha de canviar a /dashboard/rooms?difficulty=hard&search=zombi de manera que si l'usuari refresca la pàgina, els filtres es mantinguin aplicats.

### 4. Monitorització en Temps Real (Rutes Dinàmiques: /dashboard/rooms/:roomId/live)

* Quan l'operador fa clic en una sala específica de la llista, navega a aquesta URL dinàmica.
* Captura de Paràmetres: Utilitza el codi de la sala de la URL (ex: laboratori-zombi) per carregar les dades de la partida actual.
* Panell de Control Live: Mostra un temporitzador en compte enrere de 60 minuts i un històrial de "pistes enviades".
* Navegació programàtica d'emergència: Afegeix un botó vermell de "PÀNIC / ABANDONAR". En prémer-lo, el sistema ha de demanar confirmació i redirigir automàticament a l'operador de tornada a /dashboard mitjançant codi, llançant una alerta global.

### 5. Gestió d'Errors (path: "*")

* Si l'operador s'equivoca escrivint a la barra d'adreces (ex: /dashboard/roomz), s'ha de mostrar una pàgina personalitzada d'Error 404 estilitzada amb la temàtica de "Codi d'Accés Incorrecte / Seqüència de Seguretat Activada" amb un botó per tornar de manera segura a l'inici.


