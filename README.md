# Daily Error Report Workflow (n8n)

Ten projekt zawiera workflow stworzony w [n8n](https://n8n.io), który automatycznie generuje i wysyła dzienny raport błędów na podstawie danych wejściowych.

## Skład workflowa

Workflow składa się z następujących kroków:

1. **Uruchom raport (Manual Trigger)**  
   Ręczne rozpoczęcie workflowa (np. do testów lub prezentacji).

2. **Dane testowe (Set)**  
   Wprowadza przykładowe dane w formacie JSON zawierające błędy:
   ```json
   {
     "errors": [
       {
         "data": "2025-07-07",
         "linia": "B",
         "typ_błędu": "Błąd jakości",
         "czas": "08:30"
       }
     ]
   }
   ```

3. **Warunek: Czy data błędu to dzisiaj? (If)**  
   Sprawdza, czy błąd wystąpił dzisiaj.

4. **Mail z błędami (EmailSend)**  
   Wysyła wiadomość e-mail zawierającą szczegóły błędu, jeśli dane dotyczą bieżącej daty.

5. **Mail bez błędów (EmailSend)**  
   Wysyła pozytywny raport ("Wszystko działa poprawnie! ✅"), jeśli nie ma błędów dzisiaj.

## Konfiguracja e-maila

W obu nodach EmailSend używany są przykładowe e-maile, w razie potrzeby należy zmienić je na własne:
- `From`: `example@example.com`
- `To`: `recipient@example.com`
- Konto SMTP: `SMTP account` (zdefiniowane w n8n).

## Wymagania

- Zainstalowany i skonfigurowany n8n.
- Ustawione poświadczenia SMTP w n8n.
  
## Możliwości rozbudowy

- Pobieranie błędów z bazy danych, API lub pliku.
- Obsługa wielu błędów.
- Formatowanie HTML raportu.
- Wysyłka raportu do wielu odbiorców.

## Testowanie

Workflow zawiera wbudowane dane testowe – wystarczy kliknąć **"Execute workflow"**, aby sprawdzić działanie.

---

Plik źródłowy workflowa: `My workflow 2.json`
