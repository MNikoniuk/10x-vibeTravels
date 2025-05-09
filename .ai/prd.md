# Dokument wymagań produktu (PRD) - VibeTravels

## 1. Przegląd produktu
VibeTravels to webowa aplikacja MVP do planowania wycieczek trwających od 3 do 14 dni. Użytkownicy tworzą notatki dotyczące miejsc i preferencji, a moduł AI generuje trzy alternatywne harmonogramy oraz dodatkową opcję dla każdej atrakcji. Plan można edytować, oszacować koszty i zapisać z tytułem (lokalizacja + daty).

## 2. Problem użytkownika
Użytkownikom trudno ręcznie zestawić interesujące atrakcje, zoptymalizować trasę i oszacować koszty podróży. Poszukują narzędzia, które:
- zamieni luźne notatki i cele w kompletny harmonogram,
- automatycznie ustali kolejność odwiedzanych punktów,
- oszacuje łączny koszt wycieczki,
- umożliwi szybkie edytowanie i zapis gotowego planu.

## 3. Wymagania funkcjonalne
1. Autoryzacja i uwierzytelnianie
   - rejestracja i logowanie e-mail/hasło
2. Profil użytkownika
   - wypełnianie i edycja preferencji turystycznych (aktywny/spokojny styl, budżet dzienny, ulubione kategorie)
3. Notatki podróżnicze (CRUD)
   - pola: lokalizacja, daty, zakres cen, budżet dzienny, poziom aktywności, typ atrakcji (dynamiczne/spokojne)
   - predefiniowane kategorie (min. 10): zabytki, muzea, parki, plaże, góry, restauracje, życie nocne, aktywność na świeżym powietrzu, zakupy, relaks i spa
   - możliwość dodawania własnych kategorii
4. Generowanie planu przez AI
   - komunikacja przez plik tekstowy z retry do 5 prób
   - po 5 nieudanych próbach wyświetlenie komunikatu o błędzie
   - optymalizacja trasy, odrzucenie nadmiarowych atrakcji
   - wyniki: 3 warianty harmonogramu + 1 alternatywa dla każdej atrakcji
5. Edycja harmonogramu planu
   - zmiana kolejności (drag-and-drop), dodawanie i usuwanie notatek
   - popup ostrzegający o niezapisanych zmianach
6. Szacowanie kosztów
   - przycisk "Oszacuj koszt podróży" w panelu podsumowania
   - walidacja całkowitego budżetu (suma kosztów transportu, noclegów, wyżywienia, atrakcji, innych)
7. Zapis i przegląd planów
   - wymóg wprowadzenia tytułu (lokalizacja + daty) przed zapisem
   - zakładka "Podróże" z listą zapisanych planów (tytuł, daty, opcje otwarcia i usunięcia)

## 4. Granice produktu
- brak współdzielenia planów między kontami
- brak zaawansowanej analizy multimediów (zdjęcia)
- brak integracji z systemami rezerwacyjnymi i logistycznymi
- desktop-only, bez responsywności mobilnej

## 5. Historyjki użytkowników

US-001
Tytuł: Rejestracja i logowanie
Opis: Użytkownik tworzy konto i loguje się metodą e-mail/hasło.
Kryteria akceptacji:
- możliwość rejestracji z potwierdzeniem hasła
- logowanie poprawnymi danymi
- wyświetlenie błędu przy niepoprawnych danych

US-002
Tytuł: Uzupełnienie i edycja profilu
Opis: Użytkownik wypełnia profil preferencjami turystycznymi.
Kryteria akceptacji:
- pola preferencji zachowane po wylogowaniu i ponownym zalogowaniu
- walidacja zakresu budżetu dziennego

US-003
Tytuł: Tworzenie notatki podróżniczej
Opis: Użytkownik dodaje notatkę z polami: lokalizacja, daty, zakres cen, budżet dzienny, poziom aktywności, typ atrakcji.
Kryteria akceptacji:
- nowa notatka wyświetlana na liście
- walidacja pól (lokalizacja, daty)

US-004
Tytuł: Przegląd, edycja i usunięcie notatki
Opis: Użytkownik odczytuje, modyfikuje lub usuwa istniejącą notatkę.
Kryteria akceptacji:
- zmiany zapisywane natychmiast
- usunięcie notatki usuwa ją z listy

US-005
Tytuł: Dodawanie własnych tagów do kategorii
Opis: Użytkownik dodaje nowe tagi do listy kategorii.
Kryteria akceptacji:
- co najmniej 10 domyślnych kategorii dostępnych
- dodane tagi pojawiają się w selektorze

US-006
Tytuł: Generowanie planu przez AI
Opis: Użytkownik inicjuje generowanie planu; system komunikuje się z AI przez plik tekstowy.
Kryteria akceptacji:
- plik wysłany, retry do 5 prób
- komunikat o błędzie po 5 nieudanych próbach
- widoczne 3 warianty + 1 alternatywa dla każdej atrakcji

US-007
Tytuł: Edycja harmonogramu wygenerowanego planu
Opis: Użytkownik zmienia kolejność, dodaje lub usuwa notatki w planie.
Kryteria akceptacji:
- drag-and-drop działa poprawnie
- dodanie/ usunięcie notatki odzwierciedlone w harmonogramie

US-008
Tytuł: Ostrzeżenie o niezapisanych zmianach
Opis: Przy próbie opuszczenia edycji bez zapisu wyświetlany jest popup.
Kryteria akceptacji:
- modal pojawia się przy zmianach i próbie zamknięcia
- użytkownik może anulować lub potwierdzić utratę zmian

US-009
Tytuł: Oszacowanie kosztów podróży
Opis: Użytkownik klika "Oszacuj koszt podróży" i otrzymuje podsumowanie kosztów.
Kryteria akceptacji:
- przycisk widoczny w panelu podsumowania
- walidacja, że suma nie przekracza budżetu całkowitego
- czytelne wyświetlenie wyników

US-010
Tytuł: Zapis planu z tytułem
Opis: Użytkownik wprowadza tytuł (lokalizacja + daty) i zapisuje plan.
Kryteria akceptacji:
- pole tytułu wymagane przed zapisem
- zapisany plan pojawia się w zakładce "Podróże"

US-011
Tytuł: Przeglądanie i usuwanie zapisanych planów
Opis: Użytkownik przegląda listę zapisanych planów i może je otworzyć lub usunąć.
Kryteria akceptacji:
- lista zawiera tytuł, daty, opcje "Otwórz" i "Usuń"
- usunięcie planu powoduje jego skasowanie z listy

## 6. Metryki sukcesu
- 90% użytkowników z wypełnionym profilem preferencji
- 75% użytkowników generuje co najmniej 3 plany rocznie
- średni czas od notatki do gotowego planu poniżej 5 minut
- odsetek nieudanych prób AI po retry poniżej 15%