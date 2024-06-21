Seat Ibiza i EPC -  07.04.2024
------------------------------
Kontrolka EPC sygnalizuje różne błędy z układem elektrycznym w samochodzie. Po odczytaniu błędów pokazał się w module silnika (036 906 034 AH) błąd: 16955 - Brake Switch (F): Implausible Signal.

Możliwych jest kilka przyczyn tego błędu:
- Uszkodzony czujnik pedału stop
- Nieprawidlowe lub niedzialające żarówki świateł stop
- Przepalone bezpieczniki numer 4 i/lub 26

Aby sprawdzić czujnik pedalu stop, należy w programie diagnostycznym wejść w modul Engine następnie w Measure Blocks i wybrać grupę 066

W polu Bin Bits. powinny być następujące wartość:
- 00000000 - pedał sprzęgla i hamulca NIE naciśnięty
- 00000100 - pedał sprzęgla naciśnięty
- 00000011 - pedał hamulca naciśnięty

W moim przypadku okazało się, że mimo wymiany przelącznika wciąż działał niepoprawnie. Przełącznik ma 4 piny. Piny 1 i 4 wysyłają informację sterwonikowi o wciśniętym hamulcu zaś piny 2 i 3 odpowiadają za włączenie świateł stop.
Gdy pedał NIE jest wciśnięty pin 1,4 powinny być rozwarte a 2,3 zwarte, zaś po wciśnięciu pedalu powinno być odwrotnie.
